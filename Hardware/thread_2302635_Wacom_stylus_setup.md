---
title: "Wacom stylus setup"
date: 2015-11-12
forum: Hardware
---

### Post by federico-prato-t on 2015-11-12
hei guys!


i got this wacom stylus to work by installing the linux-wacom packages from sourceforge. Especially input-wacom-0.30.0 and linuxwacom-0.11.0. The device works fine and i can finally avoid using the mouse. I just haven't understood is there a way to configure the pad so that it would allow me to scroll with it. For now i need to go and grab the sidebar and track it down to scroll the page. in my system settings i have a Wacom Tablet tab, but from there it seems my stylus is not recognized as i get "No Tablet detected. Please plug in or turn on your Wacom Tablet". I tried using xsetwacom to achieve the result i'd like, but i miserably failed :$

```
xsetwacom set 15 Button 1 key "down"
```

gives me the possibility to have one of my 4 buttons to act as the down arrow. but then i can't find a way of configuring the other three buttons. I get no errors, but

```
xsetwacom set 15 Button 2 key "up"
```

won't work :(. please help me out :)

---

