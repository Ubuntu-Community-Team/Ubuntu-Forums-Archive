---
title: "switch from ipw3945 to iwlwifi"
date: 2008-03-29
forum: Hardware &amp; Laptops
---

### Post by pizzavortex on 2008-03-29
I have an acer travelmate 3012wtmi with intel pro wireless 3945abg.  i started out with feisty and then upgraded to gutsy.  the wireless card needs a proprietary driver.

It says, "while this driver is mostly free, it relies on a piece of proprietary software to determine the channels your wireless card is permitted to use."  

the connection information states that the wireless driver is ipw3945.  despite the non-free drivers my wireless connection works fine.

earlier today I tried out the live-cd of hardy heron beta.  the wireless works fine on it but i discovered that no restricted drivers were being used.  under closer inspection I found out that this live cd uses iwlwifi, a driver which, as I understand it, has superseded ipw3945.  

my questions are:
1) Is iwlwifi a feature that is new to hardy heron?
2) Since the live-cd has no pre-configuration by the user,  is it possible that iwlwifi is something i can  use in gutsy and I am only using it because of old configuration from feisty fawn?
3)If 2 is true, how can I start using iwlwifi and ditch these irritating proprietary drivers.

---

### Post by Ayuthia on 2008-03-29
iwlwifi was introduced to the 2.6.24 kernel (which is used in Hardy).  You should be able to use this driver in Gutsy, but you will have to download and compile the driver.  Here is the link to the website:
[http://www.intellinuxwireless.org/?p=iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi)

When you click on the downloads link at their site, they also include a link on how to build the driver.  Hope that helps.

---

### Post by pizzavortex on 2008-03-29
after some more rigourous searching, i managed to make the switch to ipw3945 as the modules were already there.  it is not without its problems, for example the led is not working and if i press the on/off button for the wireless, it turns off completely and the only way i can turn it back on is by pressing it again and rebooting.  however, iwlwifi is apparently more stable and so might be the solution for these blasted crashes I am having.  if i'm luck y the leds will work in hardy becuase they did when i used the live cd.  anyway, all I can do is wait until april 24th. 

:-\"

if i am feeling especially impatient I can just install the beta release:tongue:

---

### Post by steveneddy on 2008-04-23
> **pizzavortex said:**
> after some more rigourous searching, i managed to make the switch to ipw3945 as the modules were already there.  it is not without its problems, for example the led is not working and if i press the on/off button for the wireless, it turns off completely and the only way i can turn it back on is by pressing it again and rebooting.  however, iwlwifi is apparently more stable and so might be the solution for these blasted crashes I am having.  if i'm luck y the leds will work in hardy becuase they did when i used the live cd.  anyway, all I can do is wait until april 24th. 

:-\"

if i am feeling especially impatient I can just install the beta release:tongue:

This is an old thread, but adding the backports fixed this issue.

```

sudo apt-get install linux-backports-modules-hardy-generic

```

---

