---
title: "help need running really badly for my friend thats joining the army"
date: 2010-10-07
forum: Hardware
---

### Post by cobra11murderer on 2010-10-07
1)10.04
2)AlienWare 51 - N
3)M5500
4)Prob = Intel® PRO/Wireless 2200BG

the wireless is not working at all, it wont enable it, or anything, its saying its disabled

---

### Post by TNT1 on 2010-10-07
Is it enabled in BIOS?

---

### Post by cobra11murderer on 2010-10-07
> **TNT1 said:**
> Is it enabled in BIOS?

yup

---

### Post by cobra11murderer on 2010-10-07
> **cobra11murderer said:**
> yup

i cant figure out why its not working, it has a button for it but thats not workin.., its assigned to sleep.., either way i cant get it to work any ideas??, im kinda immediate to linux, im more advanced to windows, so whatever yall want me to do ill try

---

### Post by TNT1 on 2010-10-07
Have a look here:
[http://ubuntuforums.org/showthread.php?t=309041](http://ubuntuforums.org/showthread.php?t=309041)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=309041&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=309041&page=2)

Same wireless card, might help

---

### Post by cobra11murderer on 2010-10-07
> **TNT1 said:**
> Have a look here:
[http://ubuntuforums.org/showthread.php?t=309041](http://ubuntuforums.org/showthread.php?t=309041)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=309041&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=309041&page=2)

Same wireless card, might help

well i tryed this and
```

eddie@eddie-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by TNT1 on 2010-10-07
Try here:
[http://ubuntuforums.org/archive/index.php/t-541953.html](http://ubuntuforums.org/archive/index.php/t-541953.html)

---

### Post by cobra11murderer on 2010-10-07
> **TNT1 said:**
> Try here:
[http://ubuntuforums.org/archive/index.php/t-541953.html](http://ubuntuforums.org/archive/index.php/t-541953.html)

sadly it did nothing, wireless is still grayed out

---

### Post by luvshines on 2010-10-07
You may want to check that what is causing the wrong functionality being assigned to the button.

Start acpi-listen and press the button.
It will give some code. Then look for it in /etc/acpi/events, what that code is assigned to

---

### Post by cobra11murderer on 2010-10-07
> **luvshines said:**
> You may want to check that what is causing the wrong functionality being assigned to the button.

Start acpi-listen and press the button.
It will give some code. Then look for it in /etc/acpi/events, what that code is assigned to

well believe it or not i just tryed acpi-listen, and its doing nothing........, at all..it acts like nothing is happening

---

### Post by luvshines on 2010-10-07
Did you try pressing the wireless on/off toggle button after acpi-listen command ??
You said that the wireless button is actually acting as sleep button, then it should generate an event which will trigger sleep

---

### Post by cobra11murderer on 2010-10-07
> **luvshines said:**
> Did you try pressing the wireless on/off toggle button after acpi-listen command ??
You said that the wireless button is actually acting as sleep button, then it should generate an event which will trigger sleep

that i did, and i tryed all 3 of them still nothing

---

### Post by cobra11murderer on 2010-10-07
> **cobra11murderer said:**
> that i did, and i tryed all 3 of them still nothing

 a help button, and playback button, and then the wireless,forgot to mention those, but main thing is the wireless

---

### Post by xircon on 2010-10-07
What does:
```
cat /var/lib/NetworkManager/NetworkManager.state
```

Return?

---

### Post by cobra11murderer on 2010-10-07
> **xircon said:**
> What does:
```
cat /var/lib/NetworkManager/NetworkManager.state
```

Return?

NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true

---

### Post by xircon on 2010-10-07
Edit the file, change false to true and then reboot.

```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by cobra11murderer on 2010-10-07
> **xircon said:**
> Edit the file, change false to true and then reboot.

```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```

um little prob, its all read only how would i go about doing that?

---

### Post by luvshines on 2010-10-07
Well, it should not be readonly after sudo. :confused:

---

### Post by xircon on 2010-10-07
Why is it read only?  Shouldn't be, did you try the command I gave you?  I hate chmod, I can never remember the syntax :)

Try:

```
chmod a+rw /var/lib/NetworkManager/NetworkManager.state
```

Then the sudo gedit command from earlier

---

### Post by cobra11murderer on 2010-10-07
> **xircon said:**
> Why is it read only?  Shouldn't be, did you try the command I gave you?  I hate chmod, I can never remember the syntax :)

Try:

```
chmod a+rw /var/lib/NetworkManager/NetworkManager.state
```

Then the sudo gedit command from earlier

lol my whole drive is readonly pretty much root has access and i dont..i forget how to change that

---

### Post by xircon on 2010-10-07
You did type sudo didn't you?  This elevates you to root for the command that follows and asks for your password.

---

### Post by cobra11murderer on 2010-10-07
> **xircon said:**
> You did type sudo didn't you?  This elevates you to root for the command that follows and asks for your password.

lol, thats why it didnt work lol, now i put it to true

---

### Post by xircon on 2010-10-07
Big tip:

Copy commands from the forum webpage and use ctrl+shift+V to paste them into terminal.

Copy stuff from terminal - highlight with mouse and copy with ctrl+shift+C, paste into forum with ctrl+V.

Did it work?

---

### Post by cobra11murderer on 2010-10-07
> **xircon said:**
> Big tip:

Copy commands from the forum webpage and use ctrl+shift+V to paste them into terminal.

Copy stuff from terminal - highlight with mouse and copy with ctrl+shift+C, paste into forum with ctrl+V.

Did it work?

if you where talking about this
```
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
it didnt work?

---

### Post by xircon on 2010-10-07
Did you reboot?

After rebooting run the cat command again and make sure they all say true.

---

### Post by cobra11murderer on 2010-10-07
> **xircon said:**
> Did you reboot?

After rebooting run the cat command again and make sure they all say true.

it didnt work, i did that, and it reverted back to the same.., tryed it again and same thing

---

### Post by xircon on 2010-10-07
Sometimes I have had to do this a few times (edit, save, reboot).

Try it a couple more times, just in case. Also this may work, does for some, but never has for me:

```
 
sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

```

Other than that I am stumped.

---

### Post by cobra11murderer on 2010-10-07
> **xircon said:**
> Sometimes I have had to do this a few times (edit, save, reboot).

Try it a couple more times, just in case. Also this may work, does for some, but never has for me:

```
 
sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

```

Other than that I am stumped.

thanks for tryin, im stumped to, its still didnt work..i have no idea maybe some one else will think of somthing

---

### Post by xircon on 2010-10-07
Final thought, does the wireless work if you boot of the live CD?

---

### Post by sikander3786 on 2010-10-07
Did you seee this post. It is intended for Intel Pro Wireless cards, so if you follow it correctly, you should get it working.

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

---

### Post by cobra11murderer on 2010-10-07
> **xircon said:**
> Final thought, does the wireless work if you boot of the live CD?

live cd didnt work same old thing

---

### Post by cobra11murderer on 2010-10-07
> **sikander3786 said:**
> Did you seee this post. It is intended for Intel Pro Wireless cards, so if you follow it correctly, you should get it working.

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

nope didnt work, its not even starting the card.., i know the card works cause i tryed it in another laptop..

---

### Post by cobra11murderer on 2010-10-07
> **cobra11murderer said:**
> nope didnt work, its not even starting the card.., i know the card works cause i tryed it in another laptop..

i swapped it out just now with another chip and its being read but its not seeing the network.., its a realateck any ideas on that, maybe more likely to get that one working than this other one

---

