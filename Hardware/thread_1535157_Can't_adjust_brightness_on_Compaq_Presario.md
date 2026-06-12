---
title: "Can't adjust brightness on Compaq Presario"
date: 2010-07-20
forum: Hardware
---

### Post by alexjohnc3 on 2010-07-20
I have a Compaq Presario CQ62, but I am unable to adjust the brightness. Because of this, the battery life is quickly drained when I unplug my laptop. The function keys and the Brightness Applet don't do anything. Any ideas?

---

### Post by Sonador on 2010-07-20
Hi, I've just on my acer (with gma 4500) done this: [http://ubuntuforums.org/showpost.php?p=9614117&postcount=3](http://ubuntuforums.org/showpost.php?p=9614117&postcount=3)

but as i said, i have acer, i dont know your compaq, maybe some easier solution for your model exists, like editing grub (nomodeset, acpi_backlight=vendor etc.) search the forums for this.

---

### Post by alexjohnc3 on 2010-07-20
Do I just run those in the terminal? And is there a chance of it damaging my Ubuntu install? I've been using Ubuntu for a while, but I'm still kind of a novice with it. =\

---

### Post by alexjohnc3 on 2010-07-21
Okay, well I figured out what it wanted me to do, which was pretty simple. It didn't do anything, though. I noticed I couldn't set the shortcut key to F2 or F3, which are they keys that are supposed to change the brightness (I used another key, and pressing it ran the script. Nothing happened accept a window asked for my password the first time). Ubuntu doesn't seem to recognize them for some reason. It works with F10 and F11, which are the volume controls, though.

---

### Post by alexjohnc3 on 2010-07-23
Can anyone help? It would be greatly appreciated since I'm really stuck. :(

---

### Post by Sonador on 2010-07-24
Im not sure if i understand right, is there a problem, that the change of brightness doesnt work at all or it works but you can not add the desired shortcut?

concernig the functionality of the scripts, you can check it out by running single command in terminal, eg.:
```
sudo setpci -s 00:02.0 F4.B=42 
```   (brightness for 30%)
```
sudo setpci -s 00:02.0 F4.B=ff
```    (brightness for 100%)

concernig the shortcuts, do you add it as "fn+F2" or "ctrl+F2" or how?

---

### Post by alexjohnc3 on 2010-07-24
The issue is I can't change the brightness. When I type in the first command I get this error: "setpci: Warning: No devices selected for `F4.B=42'."

---

### Post by Sonador on 2010-07-25
Type in terminal ```
lspci
``` look for a line with "VGA compatible controller...", the line begins with some numbers (I have 00:02.0). If you have before "VGA comp..." different numbers, put the correct numbers in the command I have typed in the previous reply (...setpci...) and see if it works now.

But if you have "00:02.0 VGA compatible controller..." too from lspci output Im afraid i cant help anymore.

---

### Post by alexjohnc3 on 2010-07-25
For me is said: "01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]"

I typed in "sudo setpci -s 01:05.0 F4.B=42", but nothing changed. It didn't give an error message this time, though.

---

### Post by Sonador on 2010-07-28
Its beyond my skills now, i dont know why it doesnt work, maybe this command just dont work on your hardware.

You can wait if somebody else helps or you may try another solution for example the grub editing, like adding various: acpi_backlight=vendor, nomodeset etc. it was often discussed on ubuntuforums, you can search it. Dont forget to try changing brightness using brightness applet, for someone it works.

---

### Post by nanonils on 2010-08-05
> **alexjohnc3 said:**
> I have a Compaq Presario CQ62, but I am unable to adjust the brightness. Because of this, the battery life is quickly drained when I unplug my laptop. The function keys and the Brightness Applet don't do anything. Any ideas?

Have the same laptop and the same problems. Brightness app does not work.

In another thread I was trying to fix the WiFi but that didn't work either (have the CQ63-228DX). Hopefully we can figure it out - given the steal price at BB I'm sure we're not the only ones who put ubuntu on it.

---

### Post by Brotherbrat13 on 2010-08-05
Same here. 

Compaq Presario CQ62-231NR. The Audio Controls work (Can't get my speakers to work though..), but not the brightness controls. Everything else works as well.. The Calculator button, email, screen lock, ect.

On a side note.

On AC power, you can go into Power Management and adjust the brightness from there, but only for AC power. On Battery, its either the Max or the Min. with no slider like for AC power.

---

### Post by nanonils on 2010-08-05
Very good. Min brightness when trying to save doesn't sound so bad. Thanks for the tip. 

Have you checked out this thread to fix your sound? [http://ubuntuforums.org/showthread.php?t=1531187](http://ubuntuforums.org/showthread.php?t=1531187)
I can adjust mine and don't have issues with the internal speakers (or do you mean external speakers?).

Can't figure out why my wifi is up out doesn't permit data transfer. Realtek drivers are supposedly in the kernel. Yours is working alright?

---

### Post by Brotherbrat13 on 2010-08-05
Thanks for the link to the thread, I'll try that out later.

At first I was confused as to why my Wifi wasn't working. It stumped me. I could use it for a few seconds, then it would stop. 

I got it working by updating. When data is constantly coming over the Wifi, it stays connected. The updates fixed it. Not sure which one though... But yes, It works just fine.

Also, I've noticed that when Ubuntu first starts up, with our wifi card atleast, it only finds wireless N signals. As time goes on, it finds the G's, then finally B. It takes a while though, but it could make wireless on ubuntu appear to be broken if you have a B/G router.

---

### Post by alexjohnc3 on 2010-08-05
> **nanonils said:**
> Have you checked out this thread to fix your sound? [http://ubuntuforums.org/showthread.php?t=1531187](http://ubuntuforums.org/showthread.php?t=1531187)
I can adjust mine and don't have issues with the internal speakers (or do you mean external speakers?).
I used that thread to fix my sound too, and I connected my laptop to an ethernet cable and updated it to get the wireless working. The only thing I can't figure out is the brightness. Everything else is pretty much fine.


> **Brotherbrat13 said:**
> On Battery, its either the Max or the Min. with no slider like for AC power.
I don't see that option. =\

---

### Post by Brotherbrat13 on 2010-08-06
Go to System -> Preferences -> Power Management.   Go over to "On Battery Power" and you should see "Reduce Backlight Brightness". If it's checked, Your at the Min Brightness. If Unchecked, the Max. Atleast, thats how it appears. It could be 20 - 80 or something along those lines.

Also, the sound fix worked. Thanks!

---

### Post by alexjohnc3 on 2010-08-06
> **Brotherbrat13 said:**
> Go to System -> Preferences -> Power Management.   Go over to "On Battery Power" and you should see "Reduce Backlight Brightness". If it's checked, Your at the Min Brightness. If Unchecked, the Max. Atleast, thats how it appears. It could be 20 - 80 or something along those lines.
That doesn't change anything for me when I'm on battery power. The brightness stays the same. =\

---

### Post by nanonils on 2010-08-06
> **Brotherbrat13 said:**
> Also, I've noticed that when Ubuntu first starts up, with our wifi card atleast, it only finds wireless N signals. As time goes on, it finds the G's, then finally B. It takes a while though, but it could make wireless on ubuntu appear to be broken if you have a B/G router.


That's a good thought. I think I will have to post in the WiFi section to trouble shoot that. Occasionally I get a very brief connect that allows me to get the Google home page and Google news but then there is no more data getting through although WiFi continues to be up. I have a LINKSYS WRT160NL R router that should be just fine with the N protocol.

I wonder what exactly the differences are between your  CQ62-231NR and my CQ63-228DX (in fact I can't even find my specs via google). Would be odd if the WiFi card were different.

Posted details about WiFi output here: [http://ubuntuforums.org/showthread.php?p=9685134#post9685134](http://ubuntuforums.org/showthread.php?p=9685134#post9685134)

---

### Post by Brotherbrat13 on 2010-08-06
> **alexjohnc3 said:**
> That doesn't change anything for me when I'm on battery power. The brightness stays the same. =\


Your right. After updating, it doesn't work anymore. Odd.

I tried using the brightness applet. It doesn't spit out any errors, but it doesn't adjust the brightness.


> **nanonils said:**
> 
I wonder what exactly the differences are between your  CQ62-231NR and my CQ63-228DX (in fact I can't even find my specs via google). Would be odd if the WiFi card were different.


...Does compaq even have a CQ63 Model yet? I can't find ANYTHING about a CQ63 on google, at all. There is, however, a CQ62-228DX.

But yes, we have the same card. The Realtek 8171 (rev 10).

In the other thread you posted, I grabbed this.
>  $ iwconfig wlan0
wlan0 802.11bgn ESSID:"nostrum" Nickname:"rtl8191SEVA2"
Mode :Managed Frequency=2.412 GHz Access Point: 00:23:69:98:2F:5E
Bit Rate=65 Mb/s
Retry: on RTS thr: off Fragment thr: off
Encryption key: [deleted by poster] Security mode: open
**[COLOR=Red]Power Management: off[/COLOR]**
Link Quality=88/100 Signal level=-54 dBm Noise level=-114 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 Mine is much different.

iwconfig wlan0
wlan0     802.11bgn  ESSID:"Wizard"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:25:9C:A5:88:21   
          Bit Rate=120 Mb/s   
          Retry: on   RTS thr: off   Fragment thr: off
          **[COLOR=Red]Power Management period:0us  mode:All packets received[/COLOR]**
          Link Quality=82/100  Signal level=-58 dBm  Noise level=-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by utilitytrack on 2010-08-06
to **alexjohnc3**

Look in here: [http://ubuntuforums.org/showthread.php?p=9685338#post9685338]("http://ubuntuforums.org/showthread.php?p=9685338#post9685338")

---

### Post by Brotherbrat13 on 2010-08-06
> **utilitytrack said:**
> to **alexjohnc3**

Look in here: [http://ubuntuforums.org/showthread.php?p=9685338#post9685338](http://ubuntuforums.org/showthread.php?p=9685338#post9685338)


Putting this into the terminal,    

echo 0 > /sys/class/backlight/acpi_video0/brightness

I get this, as the output.

bash: /sys/class/backlight/acpi_video0/brightness: Permission denied


(I have the same problem as alexjohnc3)

---

### Post by utilitytrack on 2010-08-06
to **Brotherbrat13**

Remember forever: when you get "Permission denied" shell message it's tell to you that you don't have enough rights for run anything. In order to get needed rights type [FONT="Courier New"]sudo[/FONT] in the begin of command or become root some other way.

PS 
A [FONT="Courier New"]sudo[/FONT] will not help you in this case, it don't give full rights to you, because only root can write into [FONT="Courier New"]/sys[/FONT] and [FONT="Courier New"]/proc[/FONT] directories.

---

### Post by alexjohnc3 on 2010-08-11
I'm not entirely sure why, but when I reinstalled Ubuntu, before updating it, the brightness could be adjusted. After updating it, I was able to adjust the brightness still. Not sure why.

---

### Post by Brotherbrat13 on 2010-09-11
Its fixed in the 10.10 Beta, but you need to use the brightness applet. The keys still don't work.

Sorry for the necro.

---

