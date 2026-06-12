---
title: "HELP PLEASE!!! kubuntu 8.10"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by mor377 on 2009-04-13
Ok well I had a wondows xp computer and i hade the live xd for kubuntu 8.10 and i went in and use the guided method to use the whole hard drive... when i start up my computer it goes through the boot pocess and then it gets to my login, so i type my password and it starts to load...

and when it has the hard drive then the settings and so on icons ans fade in, well mine stops and freeses af the desltop icon... i can still move my muse but i cant click and it jsut sits there and i cant do anything...

it may be a problem with my ram? i dont know how much i need to run kubunto 8.10 but i think i have from 512 mb to 1 gb... seeing as i cant get to my desktop i cant really find a way to check it... 

any help would be appreaciated :)

---

### Post by Chemical Imbalance on 2009-04-13
This is a problem I've had before and this seems to fix it (don't worry about deleting this file, it regenerates again upon login):


When you get to your login screen, press ctrl+alt+F1 and login at the prompt.

Type:

```
sudo rm ~/.ICEauthority
```

then press ctrl+alt+F7 to login again

There was a bug I believe that put the wrong permissions on that file, and by deleting it, it will regenerate with your user permissions and allow you to login.





Here is a thread I found about it:[http://ubuntuforums.org/showthread.php?t=206985](http://ubuntuforums.org/showthread.php?t=206985)
This problem pops up every year it seems

---

### Post by wernerportwig on 2009-04-14
This worked for me

1.	From the Grub boot menu slect the “recovery mode” option.
2.	Select “root Drop to root shell prompt”
3.	Type the following at the prompt:
4.	sudo apt-get remove compiz
5.	exit
6.	Select “root Drop to root shell prompt”
7.	sudo apt-get remove compiz-core
8.	exit
9.	Select “resume Resume normal boot”

---

### Post by mor377 on 2009-04-14
> **Chemical Imbalance said:**
> This is a problem I've had before and this seems to fix it (don't worry about deleting this file, it regenerates again upon login):


When you get to your login screen, press ctrl+alt+F1 and login at the prompt.

Type:

```
sudo rm ~/.ICEauthority
```

then press ctrl+alt+F7 to login again

There was a bug I believe that put the wrong permissions on that file, and by deleting it, it will regenerate with your user permissions and allow you to login.





Here is a thread I found about it:[http://ubuntuforums.org/showthread.php?t=206985](http://ubuntuforums.org/showthread.php?t=206985)
This problem pops up every year it seems



well its not the problem about me not having the permition, it allows me in every so often then frezes again, last night i tried putting in the live cd and it boots and gets to the desktop then frezes, and when i run from the hard drive i have to boot and then press esc key to go to the recouvery then i have to boot from the recouvery

after i boot it from there, i type in my pass and then when the icons come in they freeze but i found that i had to click my mouse when the hard drive icon comes in and it loads my desktop... once my desktop is done loading it freezes up and i cant do anything... but i will try the second method later tonight seeing as im using aschools computer heeh

thanks again

---

### Post by mor377 on 2009-04-14
sorry for double posting but i tried both methods...

Chemical Imbalance, you method came up with telling me the waranty and stuff and when i logged back in it still froze up on me

and

wernerportwig i tried your method but it said that the package couldnt be located or sumtin like that, like i have a wireless card in my computer and i would think i need to connect to the internet and receive the packages from the recouvery, but i need to get to my desktop to connect to it :S

i might just post a vid or sumtin

thanks for the help so far :D

---

### Post by Chemical Imbalance on 2009-04-14
Sorry that didn't fix it,

hope you find the solution.

---

### Post by mor377 on 2009-04-14
Ok well thanks for the advice any way 

heres the link to the vid

[http://www.youtube.com/watch?v=TpDuK9Z_E3g](http://www.youtube.com/watch?v=TpDuK9Z_E3g)

---

### Post by Chemical Imbalance on 2009-04-14
Hmmm, watched the youtube vid and that looks like it could be a bug to me.  I have no clue why it would lock up like that.  I'll get back to you if I find any answers.  Also could you try the ctrl+alt+f1 method to run this:

```
sudo apt-get install fluxbox
```

This will install a very light desktop to login to.  Go back to your graphical login screen and go to the sessions button after you install fluxbox and choose "fluxbox session" or whatever its called.

If you can login to fluxbox successfully, then its probably a bug with KDE4 desktop.

---

### Post by mor377 on 2009-04-14
well wouldnt i have to connect to the internet to download the package? or is it already in the software? cuz i mean ive never been able to get to the actual desktop ever and try stuff out, like i still need to aquire my home wireless? ile try it now and post what happens tmrw mornin

thanks for the help :D

[EDIT] 

Nope no luck -.- there is still a problem with connecting to the ubuntu server or something to download the package 

would anyone think there is a way to connect to the internet (wireless) through the shell prompt?
ile look it up but if anyone has a tut or link that would be great? (if possible?)

thx

---

### Post by Chemical Imbalance on 2009-04-15
> **mor377 said:**
> well wouldnt i have to connect to the internet to download the package? or is it already in the software? cuz i mean ive never been able to get to the actual desktop ever and try stuff out, like i still need to aquire my home wireless? ile try it now and post what happens tmrw mornin

thanks for the help :D

[EDIT] 

Nope no luck -.- there is still a problem with connecting to the ubuntu server or something to download the package 

would anyone think there is a way to connect to the internet (wireless) through the shell prompt?
ile look it up but if anyone has a tut or link that would be great? (if possible?)

thx

you can connect with the command:

```
iwconfig eth0 YourWirelessSSIDhere
``` (or replace eth0 with  wlan0 or whatever your wireless device is, check  the "ifconfig" command to see which one it is)

---

### Post by mor377 on 2009-04-16
Thanks for the help again Chemical Imbalance, but again guess what... it didnt work... i tried it and it toldme that there was no net work devices for eth0 wlan0 ath0 and one other but i forget that last one at this point...

what i did is i took my computer and brought it downstairs to where my wireless router was and i used a ethernet jack to hook it up to the modem... i booted it back up in recouvery and i tried to update packages and i still cant connect... with any of the ports for soem reason...

the line i was using was

```
iwconfig eth0 Serberus
iwconfig ath0 Serberus
iwconfig wlan0 Serberus
```

serberus is my wireless internets name... or the SSID, i know its the name but would that be the SSID? 


so the problem is still here... that i can't connect to the internet to update my packages... im thinknig thats the problem... but its prob somethinhg else that im missing?

thanks

---

### Post by SuperSonic4 on 2009-04-16
eth0 and the SSID would be largely independent...

Have you tried ```
sudo ifconfig [COLOR="Red"]wlan0[/COLOR] up
sudo iwconfig [COLOR="Red"]wlan0[/COLOR] essid [COLOR="Green"]*your essid*[/COLOR] key [COLOR="Green"]*your key*[/COLOR]
```

You may need to use ```
lspci
``` to get the make of your card (most atheros are ath0 instead of wlan0 for example although jaunty uses the (now free) ath5k driver)

The second line will only work for wep encryption: [http://wiki.archlinux.org/index.php/Wireless_Setup](http://wiki.archlinux.org/index.php/Wireless_Setup) is good for general wireless information although I'm not sure if kubuntu uses dhcpcd to dhcp connections

I had a bug with the kde desktop before and it would only go away once I'd installed nvidia's drivers from a console. Jaunty didn't have this problem, even in beta

---

### Post by mor377 on 2009-04-16
haha well sorry to ask this question... im a total noob buttt...

WHATS AN ESSID? hahaha is it the same as my SSID? serberus? (my wireless name)

but i will try it later thanks for the help

---

### Post by SuperSonic4 on 2009-04-16
I was confused too at first but yes, they are the same thing

---

### Post by mor377 on 2009-04-20
Stilllll nothing has worked... like i think the connecting to the internet worked thank you, but i still for some reason cant update my packages?!?!?1 like i mean my ram is 512 is that enough to run kubuntu? my hard drive is only 80gb cuz it was a spare, but if its my ram i need to get updated i will.

---

