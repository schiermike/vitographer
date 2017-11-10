# Vitographer

A simple script to pull data from a vcontrold daemon and push it into a carbon instance.


### Information flow

Optolink adapter -> vcontrold -> vitographer -> carbon -> graphite -> grafana

### How to calculate the daily costs

```
scale(scale(summarize(scale(scale(scale(vitodens.performance, 0.01),1.82), 11000), '1d', 'avg'), 24), 0.00006335)
```
* `0.01` - `vitodens.performance` ranges from 0 to 100% -> map to interval `[0,1]`
* `1.82` - factor I came up with to address the deviation between measured value and real value
* `11000` - 11kW (my gas heater's max power)
* summarized average value per day (in Watts)
* `0.00006335` - € per Watt, i.e. 6.335 cent per kW

### Links
- http://openv.wikispaces.com/

### Screenshots

![Alt text](screenshots/gas_heating_stats.png?raw=true "Gas Heating stats")

