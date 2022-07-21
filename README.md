# Wiz lights
Control any Philips Wiz connected lights in your network.


## Applications
- Light switches to a specific colour when you receive a notification.
- Light switches on at specific time/intervals.
- Use a motion detection trigger from an IP camera to switch on the light.
- Automatically switch on the light when the alarm goes off


## Scene IDs

```
1: "Ocean"
2: "Romance"
3: "Sunset"
4: "Party"
5: "Fireplace"
6: "Cozy"
7: "Forest"
8: "Pastel colors"
9: "Wake-up"
10: "Bedtime"
11: "Warm white"
12: "Daylight"
13: "Cool white"
14: "Night light"
15: "Focus"
16: "Relax"
17: "True colors"
18: "TV time"
19: "Plantgrowth"
20: "Spring"
21: "Summer"
22: "Fall"
23: "Deepdive"
24: "Jungle"
25: "Mojito"
26: "Club"
27: "Christmas"
28: "Halloween"
29: "Candlelight"
30: "Golden white"
31: "Pulse"
32: "Steampunk"
```


## UDP requests format
By default, Wiz lights can be communicated through UDP ports 38899/38900

```
method: Type of request to the bulb(getPilot, setPilot). Use setPilot to change bulb configuration.

params: "state":true - sets bulb to ON
        "state":false - sets bulb to OFF
        
        "dimming":100 - sets bulb brightness to 100
        Dimming values range from 10-100
        
        "sceneId":27 - sets bulb scene to Christmas.
        Refer above scene ID table for other values
        
        "r":255,"g":0,"b":0 - sets bulb to Red colour
        For finer control over individual RGB colours. Values range from 0-255.
        
        "temp":2100 - sets bulb temperature in Kelvin
        Temp values range from 2200-6000. Above 6000, light switches to Cool white.
```


## Sample UDP requests
Set bulb to **ON**, brightness to **100** and scene to **“Christmas”**
```
{"method":"setPilot","params":{"state":true,"dimming":100,"sceneId":27}}   
```

Set bulb to **ON**, brightness to **50** and colour to **Red**
```
{"method":"setPilot","params":{"state":true,"dimming":50,"r":255,"g":0,"b":0}}   
```

Set bulb to **ON**, brightness to **75** and temperature to **5000k**
```
{"method":"setPilot","params":{"state":true,"dimming":75,"temp":5000}}   
```

Set bulb to **OFF**
```
{"method":"setPilot","params":{"state":false}}   
```

## Tips
- UDP command actions in apps like Tasker, Macrodroid, Automate can be used to automate the bulb according to certain conditions and triggers.
- Use Sleep as Android app plugin integration in the above apps to switch on the bulb when the alarm goes off.
- tinyCam PRO plugin motion detection feature can be used to as a trigger to switch on bulb.


---
Tested Wiz light model: A60 B22
