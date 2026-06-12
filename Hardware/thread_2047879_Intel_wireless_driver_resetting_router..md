---
title: "Intel wireless driver resetting router."
date: 2012-08-25
forum: Hardware
---

### Post by Sheepish on 2012-08-25
Hey guys,

I appreciate this may have been asked before but I've searched and searched for a definitive solution to no avail.

Okay, so I have a Samsung RV520 laptop which I recently purchased and got a bit fed up of Windows 'Infinite' Update and decided that I'd give Ubuntu a try again. As Debian based Linux have been my preference in the past I thought I'd give it a go. I used Hoary Hedgehog up to Fiesty Fawn before.

Anyway, connecting wirelessly to my Thomson router works fine, but the instant that I try to access a webpage the router resets, as if you pressed the reset button. 

Read one solution was to disable the 'N' capability, but the iwlagn config file doesn't exist anywhere in my etc file

Wired connection works absolutely fine 100% of the time.

This also happens with Linux Mint current release, if this helps.

If you need any tech details I'll have a look, I'm a tad out of touch with linux...


Many thanks,

Joe

---

### Post by ahallubuntu on 2012-08-25
What is the model of your router?

What type of router security are you using? WPA2?  (Please don't use WEP if you can help it - it's very insecure.)

Can you connect to the router with an ethernet cable instead of wireless?  And if you do that, does it work without resetting the router?

Have you tried updating the firmware on your router to the latest available from the manufacturer?  If you can connect via ethernet, you can do the firmware update that way.

---

### Post by Sheepish on 2012-08-26
Hi, Thanks for the reply.

My router is a Thomson TG585v8 and I'm using WPA+WPA2 for security, I tried on just WPA as one source suggested, but with the same result.

Using ethernet to connect gives me a perfect connection with no resetting issues whatsoever. Which led me to believe its an incompatability with the drivers/router.

I was informed by the guy at Plusnet that this router only has one version of firmware, which seems unlikely so I'll look it up.

If you need nay more details, give me a shout.

---

### Post by steeldriver on 2012-08-26
I've never heard of a router being reset by a client connection - that sounds very strange - however it *is* often necessary to disable wireless N on many of the Intel devices/drivers to get them to connect properly (I just had to do the same on a Thinkpad with iwl4965). 

AFAIK there won't be a conf file by default but if you add one it will get read when the module loads. The first step though is to see whether disabling N actually fixes anything, which you can do without modifying any files.

If you are sure your driver is iwlagn you can try

```
sudo modprobe -rf iwlagn
sudo modprobe iwlagn 11n_disable=1
```If the connection comes back up and works this time, *then* you can make it persistent by creating a conf file - afaik it doesn't matter what the name is (apart from the .conf extension) but iwlagn.conf would be a good choice

```
sudo nano /etc/modprobe.d/iwlagn.conf
```(or whatever text editor you like) and add the single line

```
options iwlagn 11n_disable=1
```

---

### Post by Sheepish on 2012-08-27
Ok, so I've tried the first terminal commands that you wrote. That seems to fix the issue. Although my driver seems to be 'iwlwifi' instead. 

Before I go any further, I'd like to say I'm not  a tech idiot! I'm a MS and apple system tech and trying to expand my skillset.

You say to make this persistant I'd need to make a conf file. I tried editing it and saving as 'iwlwifi.conf' but I don't have permissions. I assume that I'd need to run as root? Is there a way of doing this under the gui, or would I have to use nano or vi? (that is if Linux includes vi!) It would be handy to have Windows' equivalent of 'Run as administrator' in this instance.

I'd have ask if you could run it by me in layman's terms, if you don't mind the hassle.

Many thanks in advance.

Joe

---

### Post by Sheepish on 2012-08-27
Steeldriver: Thank you so much for your help, I figured it out as soon as I found vi, felt at home again!!

Unforunately though, fedora seems to be a lot better suited to my laptop, I think I'll likely still come here for help though, such a great community.

I've also learned that somehow a driver that's incompatible with a router can cause it to power cycle! News to me!

Anyway, thank you again for your patience and knowledge.

Joe

---

