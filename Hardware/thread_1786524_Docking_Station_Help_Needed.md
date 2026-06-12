---
title: "Docking Station Help Needed"
date: 2011-06-19
forum: Hardware
---

### Post by jlacroix on 2011-06-19
Hello everyone. I'm using Kubuntu 11.04 on a Dell Latitude E6410. While I am at home, I use a docking station, and I'm hoping that I can get some assistance making it "behave."

The docking station itself works, if my laptop is docked before turning it on, everything works as expected. If I undock without shutting down first, or I dock my laptop while it's still turned on, I'm asking for trouble. It seems to me that whatever process controls the docking station doesn't have any intelligence as far as turning on and turning off the appropriate screens when docking and undocking.

Basically, what I want to achieve is this. When I dock, it should turn off the laptops LCD and turn on the external monitor. When I undock, the monitor should turn off and the display should return to my laptop. I found some commands while Googling that achieve this:

Dock:
```
xrandr --output DP1 --off --output HDMI1 --auto
```

Undock:
```
xrandr --output HDMI1 --off --output DP1 --auto 
```

The problem is, while I'm a very accomplished Linux user, I'm braindead as far as how to make the laptop do these commands automatically. I am hoping maybe someone can help me set this up?

---

