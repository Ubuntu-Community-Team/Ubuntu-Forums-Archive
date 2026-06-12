---
title: "Bluetooth Mouse Won't Connect after Reboot - Ubuntu 18.04 LTS"
date: 2018-04-29
forum: Hardware
---

### Post by joegry on 2018-04-29
Ubuntu 18.04 LTS

device: Bluetooth Mouse M336/M337/M535

problem: mouse won't pair after restarting computer

resolution: I began by following the instructions for bluetooth 5 posted at:
 
[here (thank you Dave)]("http://mielke.cc/brltty/doc/Bluetooth.html#for-bluetooth-version-5")

I have also included them below along with the additional steps I needed to perform.

// open up a command prompt and use the bluetoothctl command

// list the available bluetooth controllers 
# bluetoothctl
[bluetooth]# list
Controller 01:23:45:67:89:AB fzidpc73

// choose the controller to work with
[bluetooth]# select 01:23:45:67:89:AB

// show/display the controller details
bluetooth]# show
Controller 01:23:45:67:89:AB
        Name: fzidpc73
        Alias: fzidpc73-0
        Class: 0x000000
        Powered: no
        Discoverable: no
        Pairable: yes
        UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
        UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
        UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
        Modalias: usb:v1D6Bp0246d0517
        Discovering: no
[bluetooth]# power on
[CHG] Controller 01:23:45:67:89:AB Class: 0x000104
Changing power on succeeded
[CHG] Controller 01:23:45:67:89:AB Powered: yes

// scan for bluetooth devices (make sure your mouse is in discovery mode before running this command)
[bluetooth]# scan on
Discovery started
[CHG] Controller 01:23:45:67:89:AB Discovering: yes
[NEW] Device 34:88:5D:87:C0:A6 Bluetooth Mouse M336/M337/M535
[bluetooth]# scan off
Discovery stopped
[CHG] Controller 01:23:45:67:89:AB Discovering: no

// turn the agent on just incase you need to supply a pin code[HTML][/HTML]
[bluetooth]# agent on
Agent registered


// note that the device might not ask you for a pin code

[bluetooth]# pair 34:88:5D:87:C0:A6
Attempting to pair with 34:88:5D:87:C0:A6
[CHG] Device 34:88:5D:87:C0:A6 Connected: yes
Request PIN code
[agent] Enter PIN code: 1234
[CHG] Device 34:88:5D:87:C0:A6 UUIDs:
        00001101-0000-1000-8000-00805f9b34fb
[CHG] Device 34:88:5D:87:C0:A6 Paired: yes
Pairing successful
[CHG] Device 34:88:5D:87:C0:A6 Connected: no

// once you have done this use the following two commands to
// complete setup

[bluetooth]# connect 34:88:5D:87:C0:A6
...
[bluetooth]# trust 34:88:5D:87:C0:A6
...

// your mouse should now work properly even after the computer has been restarted.

---

### Post by mpayetta2 on 2018-05-10
Thanks a lot for sharing this, it solved the problem for me.

---

### Post by jfd3220 on 2018-05-24
Thanks for this. I have a dual boot system with Windows 10 and Ubuntu 18.04 LTS. The info file in the bluetooth device folder was missing the LinkKey line that is referred to in other threads on how to set up a bluetooth mouse. The LinkKey line is there now after following your instructions.

---

### Post by ttoine on 2018-08-01
thanks a lot, it worked well !!!
Can't understand why devices without PIN code can't be trusted automatically on Ubuntu 18.04, even after the 18.04.01 release... a big fail from Canonical and Gnome.

You should share this solution on Ask Ubuntu, too ;-)

---

### Post by tforster2 on 2018-08-08
Thanks for sharing. This worked like a charm for my Logitech Ultrathin Touch Mouse on Ubuntu 18!

---

### Post by tamas-tarjanyi on 2018-09-12
Thank you very much!!! You saved me days of investigation. Easy to find and easy to follow solution. Thanks again!!!

---

### Post by bkowalski on 2018-10-08
Hello,

I am new to Ubuntu and Linux generally speaking so I hope you will forgive me.
I tried all the steps indicated above but when I try to connect to my mouse (Microsoft Sculpt Comfort) this is what I get:

[bluetooth]# connect C0:33:5E:07:70:66
Attempting to connect to C0:33:5E:07:70:66
Failed to connect: org.bluez.Error.Failed

The only way to get this to work is to manually put the mouse in discovery mode and re-run the connect step. It then works...
I would ideally like for this to happen automatically?
Any idea...
Thank you in advance!

---

### Post by firarottico on 2018-10-09
> **joegry said:**
> Ubuntu 18.04 LTS

device: Bluetooth Mouse M336/M337/M535

problem: mouse won't pair after restarting computer

resolution: I began by following the instructions for bluetooth 5 posted at:
 
[here (thank you Dave)]("http://mielke.cc/brltty/doc/Bluetooth.html#for-bluetooth-version-5")

I have also included them below along with the additional steps I needed to perform.

// open up a command prompt and use the bluetoothctl command

// list the available bluetooth controllers 
# bluetoothctl
[bluetooth]# list
Controller 01:23:45:67:89:AB fzidpc73

// choose the controller to work with
[bluetooth]# select 01:23:45:67:89:AB

// show/display the controller details
bluetooth]# show
Controller 01:23:45:67:89:AB
        Name: fzidpc73
        Alias: fzidpc73-0
        Class: 0x000000
        Powered: no
        Discoverable: no
        Pairable: yes
        UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
        UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
        UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
        Modalias: usb:v1D6Bp0246d0517
        Discovering: no
[bluetooth]# power on
[CHG] Controller 01:23:45:67:89:AB Class: 0x000104
Changing power on succeeded
[CHG] Controller 01:23:45:67:89:AB Powered: yes

// scan for bluetooth devices (make sure your mouse is in discovery mode before running this command)
[bluetooth]# scan on
Discovery started
[CHG] Controller 01:23:45:67:89:AB Discovering: yes
[NEW] Device 34:88:5D:87:C0:A6 Bluetooth Mouse M336/M337/M535
[bluetooth]# scan off
Discovery stopped
[CHG] Controller 01:23:45:67:89:AB Discovering: no
[FONT=Arial][COLOR=#000000][/COLOR][[COLOR=#000000]Audacity[/COLOR]]("https://audacity.onl/")[COLOR=#000000] [/COLOR][COLOR=#000000]
[/COLOR][/FONT][FONT=Arial][COLOR=#000000][/COLOR][[COLOR=#000000]Find My iPhone[/COLOR]]("https://findmyiphone.onl/")[COLOR=#000000] 
[/COLOR][/FONT][URL="https://origin.onl/"][COLOR=#000000][FONT=Arial]Orgin[/FONT]
[/COLOR][/URL]

// turn the agent on just incase you need to supply a pin code
[bluetooth]# agent on
Agent registered


// note that the device might not ask you for a pin code

[bluetooth]# pair 34:88:5D:87:C0:A6
Attempting to pair with 34:88:5D:87:C0:A6
[CHG] Device 34:88:5D:87:C0:A6 Connected: yes
Request PIN code
[agent] Enter PIN code: 1234
[CHG] Device 34:88:5D:87:C0:A6 UUIDs:
        00001101-0000-1000-8000-00805f9b34fb
[CHG] Device 34:88:5D:87:C0:A6 Paired: yes
Pairing successful
[CHG] Device 34:88:5D:87:C0:A6 Connected: no

// once you have done this use the following two commands to
// complete setup

[bluetooth]# connect 34:88:5D:87:C0:A6
...
[bluetooth]# trust 34:88:5D:87:C0:A6
...

// your mouse should now work properly even after the computer has been restarted.
You're the best to share this, it tackled the issue for me.

---

### Post by bkowalski on 2018-10-11
Thanks for re-posting the steps! At first I was a bit irritated as I tried those few times but then I realised something that could help others: you need to remove the mouse from the list of bluetooth devices. THEN can you perform these steps... In other words, I still had my mouse registered, which prevented from this recommendation to work properly. So far, so good!
So my advise to nitwits like me: delete your mouse and THEN do the steps!
:popcorn:

---

### Post by aparras.vp on 2018-10-19
Thank you very much for sharing! :D

---

### Post by stefanpoensgen on 2018-11-23
I'm trying to connect my microsoft surface precision mouse
The mouse starts working after i do the pair command, but it is laggy. After the connect & trust command the mouse works fine.
As soon as i close the terminal the mouse stops working. How could i solve this behavior?

---

### Post by vinibr87 on 2019-01-01
Hi.
I didn't had problems to connect the bluetooth mouse. The GUI worked well for me.
My problem was just when I restarted either the PC or my Mouse, because I had to pair it all over again.
[B]In my case, the main point was the last command, to make it a TRUSTED bluetooth connection.
[/B]The problem is now solved and my mouse reconnects automatically now.
Thanks for sharing!


> **joegry said:**
> Ubuntu 18.04 LTS

device: Bluetooth Mouse M336/M337/M535

problem: mouse won't pair after restarting computer

resolution: I began by following the instructions for bluetooth 5 posted at:
 
[here (thank you Dave)]("http://mielke.cc/brltty/doc/Bluetooth.html#for-bluetooth-version-5")

I have also included them below along with the additional steps I needed to perform.

// open up a command prompt and use the bluetoothctl command

// list the available bluetooth controllers 
# bluetoothctl
[bluetooth]# list
Controller 01:23:45:67:89:AB fzidpc73

// choose the controller to work with
[bluetooth]# select 01:23:45:67:89:AB

// show/display the controller details
bluetooth]# show
Controller 01:23:45:67:89:AB
        Name: fzidpc73
        Alias: fzidpc73-0
        Class: 0x000000
        Powered: no
        Discoverable: no
        Pairable: yes
        UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
        UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
        UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
        UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
        Modalias: usb:v1D6Bp0246d0517
        Discovering: no
[bluetooth]# power on
[CHG] Controller 01:23:45:67:89:AB Class: 0x000104
Changing power on succeeded
[CHG] Controller 01:23:45:67:89:AB Powered: yes

// scan for bluetooth devices (make sure your mouse is in discovery mode before running this command)
[bluetooth]# scan on
Discovery started
[CHG] Controller 01:23:45:67:89:AB Discovering: yes
[NEW] Device 34:88:5D:87:C0:A6 Bluetooth Mouse M336/M337/M535
[bluetooth]# scan off
Discovery stopped
[CHG] Controller 01:23:45:67:89:AB Discovering: no

// turn the agent on just incase you need to supply a pin code
[bluetooth]# agent on
Agent registered


// note that the device might not ask you for a pin code

[bluetooth]# pair 34:88:5D:87:C0:A6
Attempting to pair with 34:88:5D:87:C0:A6
[CHG] Device 34:88:5D:87:C0:A6 Connected: yes
Request PIN code
[agent] Enter PIN code: 1234
[CHG] Device 34:88:5D:87:C0:A6 UUIDs:
        00001101-0000-1000-8000-00805f9b34fb
[CHG] Device 34:88:5D:87:C0:A6 Paired: yes
Pairing successful
[CHG] Device 34:88:5D:87:C0:A6 Connected: no

// once you have done this use the following two commands to
// complete setup

[bluetooth]# connect 34:88:5D:87:C0:A6
...
[bluetooth]# trust 34:88:5D:87:C0:A6
...

// your mouse should now work properly even after the computer has been restarted.

---

### Post by vinibr87 on 2019-01-01
I have the same issue when I connect my bluetooth mouse and bluetooth headset at the same time on Ubuntu 18.04.
Just for comparison, the same happens with my a Macbook Air.

> **stefanpoensgen said:**
> I'm trying to connect my microsoft surface precision mouse
The mouse starts working after i do the pair command, but it is laggy.  After the connect & trust command the mouse works fine.
As soon as i close the terminal the mouse stops working. How could i solve this behavior?

---

### Post by wildmanne39 on 2019-01-01
Hello and welcome to the forum vinibr87, if you need support please start your own thread, the OP of this thread has not posted since he created the thread and it is mainly just receiving thank you posts, you can link to this one of you think it will help resolve your issue.

Old thread closed!

Thanks

---

