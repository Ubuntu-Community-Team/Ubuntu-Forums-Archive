---
title: "How to turn off bluetooth on startup?"
date: 2012-09-15
forum: Hardware
---

### Post by krtica on 2012-09-15
I can't find the way to turn off bluetooth by default on startup on Xubuntu 12.04.
While I was using Ubuntu 10.04, it was possible by creating .profile file in my home folder and adding ```
rfkill block bluetooth
``` line.
It doesn't work any more.
Is there a way to fix this on Xubuntu?

---

### Post by jonnyboysmithy on 2012-09-15
There is an entry in startup applications that says "bluetooth" that might be it. Not sure though.

---

### Post by krtica on 2012-09-15
Yes, I have tried that. It turns off bluetooth. But it also removes bluetooth indicator from panel, so users can't easily turn it on if they need it. :/

---

### Post by jonnyboysmithy on 2012-09-15
I now use cuttlefish for this very reason: [http://www.omgubuntu.co.uk/2012/09/automate-ubuntu-with-cuttlefish](http://www.omgubuntu.co.uk/2012/09/automate-ubuntu-with-cuttlefish)

Set it to turn off bluetooth when cuttlefish starts, and add cuttlefish to startup applications. This is an ugly/not so good way of doing it, but it should work.

---

### Post by krtica on 2012-09-15
First off all - THANK YOU JONNYBOY!
I'm using Ubuntu for 6 years, and I never used Cuttlefish before.
I don't know how I missed it, but it's perfect app that will solve many issues in the future.
THANK YOU!

It works. 
I made "Bluettoth OFF" reaction.
Simply, when Cuttlefish starts, bluetooth is set to OFF.
It even supports mono icons, so it looks nice.

```
cd /opt/extras.ubuntu.com/cuttlefish/share/cuttlefish/media
sudo cp tentacle_indicator.png tentacle_indicator.png.old
sudo cp cuttlefish_indicator.png tentacle_indicator.png
```

---

### Post by jonnyboysmithy on 2012-09-17
Great to hear that solved it. I'm glad you like it. :D

---

### Post by SlugSlug on 2012-09-17
```
sudo update.rcd -f bluetooth remove
```


Will stop bluetooth loading at boot

---

### Post by krtica on 2012-09-17
> **SlugSlug said:**
> ```
sudo update.rcd -f bluetooth remove
```


Will stop bluetooth loading at boot

Will it remove bluetooth indicator from panel?
Do I make it as a script in the startup app?

---

### Post by SlugSlug on 2012-09-17
just run it once

The indicator will be gone as bluetooth is not running, but if you start bluetooth then the indicator will show up

---

### Post by SlugSlug on 2012-09-17
and to restore it its

```
sudo update.rcd bluetooth defaults
```

---

### Post by krtica on 2012-09-17
Thank you, SlugSlug.

Yes, there are many ways to do it and remove indicator. But I need indicator to be visible even when Bluetooth is OFF so users can simply clik on it and activate it.

My colleagues, friends and familly use it, and they are not quite fans of command prompt :D, and they dont like Unity neither. At least most of them.

I would like some 'elegant' solution, like in 10.04, but for now Cuttlefish will do the job, and even more. So they'll continue to like using (X)Ubuntu.
:)

---

### Post by smssms on 2013-07-15
How do you make bluetooth default to off (at start-up), but have the applet there so you can easily switch it back on when you need it?

I've tried:

[LIST]
[*]Adding ```
rfkill block bluetooth
``` as a 'start-up application' script. 
[*]Adding ```
rfkill block bluetooth
``` and ```
sudo rfkill block bluetooth
``` to /etc/rc.local. 
[*]Changing  "RememberPowered =" to false in /etc/bluetooth/main.conf. 
[*]Changing  "InitiallyPowered =" to false in /etc/bluetooth/main.conf. 
[*]Uncommenting "DisablePlugins = network,input" in /etc/bluetooth/main.conf. 
[*]I could not edit /etc/default/bluetooth and change the line "BLUETOOTH_ENABLED=1" to "BLUETOOTH_ENABLED=0" as I do not have that file. Even so, I tried adding the file with that text anyway. 
[*]Looking in start-up applications for a 'bluetooth off' option that will leave the applet there. 
[*]Installing cuttlefish and setting it to turn off bluetooth when cuttlefish starts. 
[/LIST]

And after all of the above, _bluetooth is still switched on at every boot!_ 

Any ideas? 

Sony Vaio laptop running 12.04 LTS 64-bit; 0489:e036 Foxconn / Hon Hai bluetooth adapter

---

