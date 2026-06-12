---
title: "Make desktop bluetooth capable"
date: 2017-04-23
forum: Hardware
---

### Post by raleigh3 on 2017-04-23
Is this what I need to make my desktop blue tooth capable ?

I have some wireless Altec Lansing headphones I would like to use with my desktop.

[http://www.ebay.com/itm/USB-2-0-Bluetooth-Wireless-Adapter-V2-0-EDR-for-Windows-Linux-32-Bit-64-Bit-/142075682878?hash=item21145ee03e:g:YAYAAOSwkShY-lA~](http://www.ebay.com/itm/USB-2-0-Bluetooth-Wireless-Adapter-V2-0-EDR-for-Windows-Linux-32-Bit-64-Bit-/142075682878?hash=item21145ee03e:g:YAYAAOSwkShY-lA~)

---

### Post by Bucky Ball on 2017-04-24
> This mini USB Bluetooth dongle adapter ***enables wireless data connectivity between*** computers and ***Bluetooth enabled devices***.

If your headphones are bluetooth headphones, then yes, that's what you need, but you don't say anything about your headphones being bluetooth. You say 'wireless'. Both exist and there's a difference so best be clear on which you mean, wireless or bluetooth.

Wireless headphones generally come with some kind of docking station which plugs into the computer then your headphones connect wirelessly with that. Bluetooth connects directly to a bluetooth enabled computer (or another bluetooth device).

---

### Post by raleigh3 on 2017-04-24
The headphones work with my Samsung S5.

I thought that it used blue tooth ?

It is supported.

> [h=3]Connectivity[/h] 					 						 		[TABLE="class: dt-table"]
[TR="class: dtf-row field-component first component fieldlist"]
 			[TD="class: dtf-label dtf-col"]Inputs Supported
[/TD]
 			[TD="class: dtf-value dtf-col"][TABLE="class: list_table"]
[TR]
[TD]3.5mm[/TD]
[/TR]
[TR]
[TD]Bluetooth[/TD]
[/TR]
[/TABLE]

[/TD]
 		[/TR]
 		[TR="class: dtf-row field-component component fieldlist"]
 			[TD="class: dtf-label dtf-col"]Additional Features[/TD]
 			[TD="class: dtf-value dtf-col"][TABLE="class: list_table"]
[TR]
[TD]Integrated Playback Controls[/TD]
[/TR]
[TR]
[TD]Microphone[/TD]
[/TR]
[TR]
[TD]Noise Canceling Microphone[/TD]
[/TR]
[TR]
[TD]Wireless[/TD]
[/TR]
[/TABLE]

[/TD]
[/TR]
[/TABLE]


I bought it and plugged it in.

Is anything supposed to show up on the desktop ?

I want to use it along with my Bluetooth headphones to listen to sound without using my plug in headphones.

---

### Post by Bucky Ball on 2017-04-27
Launch Bluez, or install then launch, and set up the link with that. Once done, you shouldn't need to do it again.

I've only played about with bluetooth once or twice, but that's what I did.

---

### Post by raleigh3 on 2017-04-28
I installed BlueZ. Nothing happens at a command prompt and there is no menu pick for it ?

---

### Post by Bucky Ball on 2017-04-28
You don't now have a bluetooth icon in your toolbar? If so, click it and set up the headphones. Sorry. Can't help any more than that. Don't use bluetooth, as mentioned, but Bluez is the one.

Good luck.

PS: Are you sure the dongle is being picked up??? Pull it out, reboot, once at a desktop shove the dongle in, open a terminal and issue this:

```
dmesg
```

Check at the bottom of that output. See something about the bluetooth dongle? Post it here, but if it's loaded the right drivers and all is well, then the Bluez bluetooth icon should be on your taskbar. Click it and get to it. ;)

Bluez is like network manager in the sense that it shows up as an icon in the taskbar and you can access its setup from there.

---

### Post by raleigh3 on 2017-04-28
I am beginning to wonder if the headphones will work with the dongle ?

They work with a Samsung S5 cell phone.

There is no bluez icon.




> Altec Lansing MZX300-BLK Bluetooth Headphone-Black  With 6 hours of battery life and a 33 feet wireless range these  headphones will never hold you back. Available in a wide variety of  colors-wear a different color everyday to match your mood! Once done  listening simply place in the included carry patch and bring along with  you. Compatible with Apple, Android, Blackberry, Tablets, and Laptops.  The Altec Lansing Bluetooth Headphone – Black Features: Soft padded  headband and ear cups which provides hours of easy comfort Includes  carry pouch Wireless Bluetooth technology with Voice Confirmation Warm  and rich bass sound that brings the best in music Integral microphone  with wind cancellation and song navigation / telephony buttons.

I just talked to Altec Lansing.

They said the headphones only work with version 4.0 and above.

I have version 2.0 :-(

I have contacted seller to see if he will exchange mine for the newer version.

---

### Post by Bucky Ball on 2017-04-28
Version 4.0 of what? Bluez? Which version of Ubuntu are you using? If you are talking about Bluez, I'm on Ubuntu and the available version is 5.37. :-k

Or do you mean you have version 4.0 of the headphones? Slightly confused. Not unusual. :)

(Just a note: all bold (or caps) is considered shouting so best avoided. ;))

---

### Post by raleigh3 on 2017-04-28
Sorry for the caps. It occurs when I copy and paste from Ebay.

Bluetooth 4.0 CSR 4.0 Dongle Adaptor

---

### Post by Bucky Ball on 2017-04-28
Ah, now I'm with you. Not knowing about bluetooth I know not of these things.

But you learn something everyday, thankfully. :)

That still doesn't answer why you can't find Bluez anywhere ... :-k Have you tried typing 'bluez' into a terminal and hitting return? Does it launch?

---

### Post by raleigh3 on 2017-04-28
For those who want more info on Bluetooth and the different versions.

[https://en.wikipedia.org/wiki/Bluetooth#Bluetooth_4.0_.2B_LE](https://en.wikipedia.org/wiki/Bluetooth#Bluetooth_4.0_.2B_LE)

I have this bluetooth dongle.

How do I get it to output sound to my bluetooth headphones ?
```

andy@7:~$ sudo lsusb |grep Bluetooth
[sudo] password for andy: 
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

---

### Post by jeremy31 on 2017-05-01
Can you do this in terminal
```
bluetoothctl
```
This will bring up the bluetooth control in terminal, put the headphones in pairing mode then
```
power on
```
```
scan on
```

Does it discover any devices?  Use CTRL + d to quit the bluetoothctl.  If there are issues when trying the commands I would recommend getting an IOGear GBU521 USB bluetooth dongle as these Cambridge Silicon Radio devices have caused a lot of headaches in Linux

---

### Post by raleigh3 on 2017-05-01
```
andy@7:~$ bluetoothctl
[NEW] Controller 00:1A:7D:DA:71:13 7 [default]
[NEW] Device 88:C6:26:7B:C3:06 88-C6-26-7B-C3-06
[NEW] Device C8:69:CD:87:91:60 C8-69-CD-87-91-60
[bluetooth]# power on
Changing power on succeeded
[bluetooth]# scan on
Discovery started
[CHG] Controller 00:1A:7D:DA:71:13 Discovering: yes
[CHG] Device C8:69:CD:87:91:60 RSSI: -78
[NEW] Device 1D:2B:72:07:A2:24 1D-2B-72-07-A2-24
[CHG] Device 88:C6:26:7B:C3:06 RSSI: -79
[bluetooth]# 
```

I can not hear a sound from my headphones.

Do I need to unplug my speakers ?

---

### Post by jeremy31 on 2017-05-01
You may need to unplug them.  I would expect them to identify as Altec Lansing in the scan, or at least the model

---

### Post by raleigh3 on 2017-05-01
I ordered a IOGear GBU521 USB bluetooth dongle.

I am sorry that I made a mistake. :-)

> **jeremy31 said:**
> Can you do this in terminal
```
bluetoothctl
```
This will bring up the bluetooth control in terminal, put the headphones in pairing mode then
```
power on
```
```
scan on
```

Does it discover any devices?  Use CTRL + d to quit the bluetoothctl.  If there are issues when trying the commands I would recommend getting an IOGear GBU521 USB bluetooth dongle as these Cambridge Silicon Radio devices have caused a lot of headaches in Linux

I got one.

But it still will not pair with my headphones. ??

```
andy@7:~$ bluetoothctl
[NEW] Controller 5C:F3:70:80:FF:DA 7 [default]
[NEW] Device C8:69:CD:87:91:60 C8-69-CD-87-91-60
[bluetooth]# power on
Changing power on succeeded
[bluetooth]# scan on
Discovery started
[CHG] Controller 5C:F3:70:80:FF:DA Discovering: yes
[CHG] Device C8:69:CD:87:91:60 RSSI: -83
[NEW] Device 1D:2B:72:07:A2:24 1D-2B-72-07-A2-24
[bluetooth]# 

```

---

### Post by raleigh3 on 2017-05-03
Is there a way to see if someone has responded to my posts ??

Thanks

---

### Post by Bucky Ball on 2017-05-03
> **raleigh3 said:**
> Is there a way to see if someone has responded to my posts ??

Thanks

This should be directed to Forum Feedback and Help as has nothing to do with your solved support request, but ... If you check Settings, any post responded to will be there. That's not what you've been doing?

---

### Post by Bucky Ball on 2017-05-04
And you still haven't got the Bluez GUI going?

---

### Post by raleigh3 on 2017-05-04
I installed it.

 But there is no menu pick for it and bluez at CL does not work either.

Guess I will pitch two 2 useless dongles.

---

### Post by vasa1 on 2017-05-04
Why is this **[SOLVED]**? OP, you can "unsolve" it as well: see the (currently) last para in [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads:](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads:)> If you change your mind at a later time, you can follow the same procedure and you'll see that the "Mark this thread as solved" is now "Mark this thread as unsolved". Of course, you may want to explain what the reason for changing your mind is.

---

### Post by raleigh3 on 2017-05-05
I marked it as solved because I was told that a  IOGear GBU521 USB bluetooth dongle would solve my problem.

I trusted that it would.

It did not. 

I will mark it as unsolved.

Linux does see the device. 

Altec Over Ear BT.

I get this message 
  ```
Connection failed: blueman.bluez.errors DBusFailedError Host is down.
```

I think part of problem was that the blueman applet used to be unchecked.

---

### Post by efflandt on 2017-05-05
The first Bluetooth device you got works for me. I got it at Fry's for  just under $10.```
efflandt@msata512-1610:~$ lsusb | grep -i bluetooth
Bus  002 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth  Dongle (HCI mode)
```If you do not see the Bluetooth icon at top  right of your screen, I don't know if you answered which Ubuntu version  you are running. I am running 64-bit 16.10 because I originally had some  boot issues with 16.04 (blank screen through BIOS splash and grub menu  until something did graphics). But not sure where you see blueman applet unchecked.

---

### Post by raleigh3 on 2017-05-06
```
andy@7:~$ lsusb | grep -i bluetooth
Bus 003 Device 002: ID 0a5c:21e8 Broadcom Corp. BCM20702A0 Bluetooth 4.0

```

   ```
ubuntu-mate-16.04-desktop-amd64
```

---

### Post by jeremy31 on 2017-05-06
You should be able to use bluetoothctl with the pair and trust commands followed by the MAC address of the headphones
```
bluetoothctl
pair C8:69:CD:87:91:60
trust C8:69:CD:87:91:60
exit
```

My headphones are actually show the model number in bluetoothctl as ```
Device AC:9B:0A:4F:CA:FF MDR-ZX770BT
```

---

### Post by raleigh3 on 2017-05-06
I am assuming that I need the headphones on to do this.

```
andy@7:~$ bluetoothctl
[NEW] Controller 5C:F3:70:80:FF:DA 7 [default]
[NEW] Device C8:69:CD:87:91:60 C8-69-CD-87-91-60
[bluetooth]# pair C8:69:CD:87:91:60
Attempting to pair with C8:69:CD:87:91:60
[CHG] Device C8:69:CD:87:91:60 Connected: yes
[CHG] Device C8:69:CD:87:91:60 Connected: no
Failed to pair: org.bluez.Error.AuthenticationCanceled
[bluetooth]# trust C8:69:CD:87:91:60
Changing C8:69:CD:87:91:60 trust succeeded
[bluetooth]# exit
[DEL] Controller 5C:F3:70:80:FF:DA 7 [default]
```

---

### Post by raleigh3 on 2017-05-10
> **jeremy31 said:**
> You should be able to use bluetoothctl with the pair and trust commands followed by the MAC address of the headphones
```
bluetoothctl
pair C8:69:CD:87:91:60
trust C8:69:CD:87:91:60
exit
```

My headphones are actually show the model number in bluetoothctl as ```
Device AC:9B:0A:4F:CA:FF MDR-ZX770BT
```

Which one is my MAC address ?
```

andy@7:~$ bluetoothctl
[NEW] Controller 5C:F3:70:80:FF:DA 7 [default]
[NEW] Device 7B:05:FC:DB:73:23 7B-05-FC-DB-73-23
[NEW] Device 7A:D0:5F:18:70:23 7A-D0-5F-18-70-23
[NEW] Device 1D:2B:72:07:A2:24 1D-2B-72-07-A2-24
[NEW] Device C8:69:CD:87:91:60 C8-69-CD-87-91-60
```

I think I found it.

```
pair C8:69:CD:87:91:60
Attempting to pair with C8:69:CD:87:91:60
Failed to pair: org.bluez.Error.AuthenticationFailed
```

I bought the same dongle at Frys that efflandt uses. He is using version 16.10 while I am using 16.04 LTS.

Get the same message:

```
Attempting to pair with C8:69:CD:87:91:60 Failed to pair: org.bluez.Error.AuthenticationFailed
```

I can not help but wonder if there is a bug in version 16.04 that prevents ANY BT dongle from working??

I guess I could wait under the final version of 16.10 comes out.

Don't remember all the steps I did, but something different has occurred. 

According to these pics, Device_Added_And_Connected_Sucessfully.

But when I played a sound file, I heard nothing on the headphones.

I even tried it by disconnecting the external speakers.

---

### Post by raleigh3 on 2017-05-11
I installed UM 17.04.

Trying to get my BT headphones working on it.

It paired and I heard a beep in the headphones.

But I can hear no sound in the headphones when I play a sound found ?

What is going on ?

---

### Post by Bucky Ball on 2017-05-11
You possibly need to assign that device as the output device for your audio stream. Open Pulseaudio Volume Control (install from repositories if you don't have it) and experiment there with output devices.

Get an audio stream going (play a song), open PAVControl and the Playback tab. You should see the stream bobbing up and down on the level meter. If so, click the Output tab and see if your headphones are available in the device drop down (port).

---

### Post by raleigh3 on 2017-05-12
How do I open it ?

The headphones are available in the device drop down port.

Is there anyone with a AMD64 system that has a Bluetooth dongle that works ?

I have tried with every Ubuntu Mate version.

I hope someone is working on the problem.

---

### Post by Bucky Ball on 2017-05-12
> **raleigh3 said:**
> The headphones are available in the device drop down port.

Well, did you choose it, turn it up and what happened?????

> **raleigh3 said:**
> Is there anyone with a AMD64 system that has a Bluetooth dongle that works ?

There are lots of them, some maybe already on this thread. None have been able to help you so far. Not sure what difference AMD64 or otherwise would make to this, but I don't know all.

> **raleigh3 said:**
> I hope someone is working on the problem.

'The problem' seems to be restricted to you at this point so people on this thread would be the extent of those working on it. Anything that was affecting lots of people would be a bug, would be able to be replicated by other users, and would therefore be reported in Launchpad where a whole bunch of people may, or may not, be working on it. Have you checked there? It doesn't seem like anyone that's tried to help has the same issue. :-k

---

### Post by jeremy31 on 2017-05-12
I have working Bluetooth on Ubuntu 16.04 AMD64.  Sound is the most difficult to use over bluetooth now.  Check
```
pactl list short | grep blue
```

Mine shows
```
8	module-bluetooth-policy		
9	module-bluetooth-discover		
10	module-bluez5-discover	
```

Most people do not have module-bluetooth-discover loaded, to load that
```
pactl load-module module-bluetooth-discover
```

And then there is a bug somewhere that affects audio and the ability to switch between headset quality audio and high quality audio.  I found a command on askubuntu that would do the switch
```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect AC:9B:0A:4F:CA:FF\n quit"|bluetoothctl;sleep 5; echo -e "connect AC:9B:0A:4F:CA:FF\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
```

Just replace my headphones MAC address (AC:9B:0A:4F:CA:FF) with yours, use capital letters.  You could check the [bug report](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197) and see if other solutions are out there

---

### Post by raleigh3 on 2017-05-12
Am I supposed to use the MAC address of the BT dongle or the headphones?

```
andy@7:~/Scripts$ ./BlueTooth.sh
_You need to specify a profile by its name._
[NEW] Controller 5C:F3:70:80:FF:DA 7 [default]
[NEW] Device C8:69:CD:87:91:60 C8-69-CD-87-91-60
[NEW] Device 00:25:DB:46:05:EB Altec Over ear BT
[bluetooth]# disconnect C8:69:CD:87:91:60F
Device C8:69:CD:87:91:60F not available
[bluetooth]#  quit
[DEL] Controller 5C:F3:70:80:FF:DA 7 [default]
[NEW] Controller 5C:F3:70:80:FF:DA 7 [default]
[NEW] Device C8:69:CD:87:91:60 C8-69-CD-87-91-60
[NEW] Device 00:25:DB:46:05:EB Altec Over ear BT
[bluetooth]# connect C8:69:CD:87:91:60F
Device C8:69:CD:87:91:60F not available
[bluetooth]#  quit
[DEL] Controller 5C:F3:70:80:FF:DA 7 [default]
```

> **Bucky Ball said:**
> Well, did you choose it, turn it up and what happened?????


There are lots of them, some maybe already on this thread. None have been able to help you so far. Not sure what difference AMD64 or otherwise would make to this, but I don't know all.



'The problem' seems to be restricted to you at this point so people on this thread would be the extent of those working on it. Anything that was affecting lots of people would be a bug, would be able to be replicated by other users, and would therefore be reported in Launchpad where a whole bunch of people may, or may not, be working on it. Have you checked there? It doesn't seem like anyone that's tried to help has the same issue. :-k

Nothing.

Does it seem unusual that out of 3 different BT dongles, none works on my system ?

My headphones are Altec Lansing which produces well made products.

---

### Post by Bucky Ball on 2017-05-12
> **raleigh3 said:**
> Does it seem unusual that out of 3 different BT dongles, none works on my system ?

Yes, it does. Jeremy31 seems to be providing the most promising leads.

> **raleigh3 said:**
> My headphones are Altec Lansing which produces well made products.

Generally, yes they do. ;)

---

### Post by raleigh3 on 2017-05-12
His script did not work.

I guess the next question is for those with AMD64 systems.

What kind of BT headphones do you use that work on UM 16.04 ?

---

### Post by jeremy31 on 2017-05-12
I am using Sony MDR-ZX770BT and I have a small pod speaker called iHome iBT60 and another headset Philips SHB4000.  I have used these with the GBU521 dongle and the internal Atheros bluetooth chipset in 16.04

---

### Post by raleigh3 on 2017-05-12
Thanks.

I found a gently used Sony MDR-ZX770BT for bid on Ebay.

Current bid is $11 with one day left.

I will make a bid.

---

