---
title: "Work around for PROLINK PHS300 HSUPA USB MODEM."
date: 2009-12-09
forum: Hardware
---

### Post by nebileix on 2009-12-09
After spending 1 week of searching around, finally found a way to make it work!

By default, it was not recognised in jaunty and karmic. You can use usb_modeswitch to change the modem mode but it'll be even easier to eject it. Thats why i created this script for the ease of own usage.

Something to take note:

The device doesn't activate scanning of available network in Linux. The led light will always be red. In order for it to scan, you have to plug it into a widoze machine and install whatever crap it comes with, wait for the led light to change(any color but red) and plug out without using the safe remove device in widoze. 

If you are interested in modifying it to your mobile BB device, please feel free to do so and share with others. One of the interesting guide to start [http://tuxmobil.org/linux_on_laptops_with_umts_cards.html]("http://tuxmobil.org/linux_on_laptops_with_umts_cards.html"). Google it and there're more out there.

PS: If you are not sure of what u are doing, please don't try on other device other then the above mention as I can't promise that it'll work or break anything.

Do remember to change the permission for exec.

---

### Post by Kevin- on 2010-01-15
Hi nebileix , I've tried running the script from nautilus just clicking run or run in terminal to no effect ... am I missing out on anything ? 

i have the phs300 and running the latest kernal (x.17 i think) 
had also tried various ways but didn't manage to get it running ... 

would appreciate your help :)

oh i'm a noob.... 
how can i execute your file in terminal ? currently i'm running it from a sudo nautilus ... 
I did notice the following errors : 

WARNING: All config files need .conf: /etc/modprobe.d/blacklist-vmc, it will be ignored in a future release.

/3gusb: line 15: gnome-ppp: command not found

updated: 
I manage to uninstall my previous modem tool -vodafone betavine.
installed gnome ppp 
got the pop up box .... 

not sure how I can connect to my M1 broadband line ... 
was in setup when tried to detect usb modem an error "no modem was found in your system" 
any idea how to proceed?

---

### Post by renu on 2010-01-15
I have same problem as kevin!!!!
 
line 15: gnome-ppp: command not found

---

### Post by nebileix on 2010-02-16
Sorry for the late reply guys.

U'll need gnome-ppp to work. A few things to check first:

1) Which ubuntu u are using?

2) Did u manage to get the led blue or purple after u plug in?

---

### Post by nebileix on 2010-02-16
> **Kevin- said:**
> 
not sure how I can connect to my M1 broadband line ... 

Use the usb modem in windows and check the settings over there. Please do take note of the usb modem is not activated by default. You need to activate it via windows system as well. Wait for the led on the modem to be blue or red, then plug out straight without using windows eject hardware.

> **Kevin- said:**
> 
was in setup when tried to detect usb modem an error "no modem was found in your system"
any idea how to proceed?

do```
ls /dev/ttyU*
``` in the terminal and see what is available and let me know. Should select ttyUSB2 in gnome-ppp settings.

---

### Post by Kathees on 2010-05-26
Hi everyone,

So I have downloaded the script and tried to run that. At first it says 'gnome -ppp' command not found. 

So after I downloaded and installed gnome-ppp-0.3.23.tar.bz2

Then again tried to run the script it shows a popup and ask to enter a user name password which I have no idea what it is.

What should I do after this point?

My ubuntu version is Latest 10.04

Thanks in advance

---

### Post by nebileix on 2010-06-10
> **Kathees said:**
> Hi everyone,

So I have downloaded the script and tried to run that. At first it says 'gnome -ppp' command not found. 

So after I downloaded and installed gnome-ppp-0.3.23.tar.bz2

Then again tried to run the script it shows a popup and ask to enter a user name password which I have no idea what it is.

What should I do after this point?

My ubuntu version is Latest 10.04

Thanks in advance

Sorry for late reply. For the username and password in the gnome-ppp, will need to depend on ur mobile broadband telco. For my case, my telco dun actually required any username and password. But gnome-ppp would required those field to be filled in. So just input anything in there. If you are using 10.04, you might not need to use the script as from what im aware, the network-manager are able to recognise the device now using modem manager. All you need to do is to eject the device by 

```
$ eject /dev/"sr1"(Replace sr1 with whatever it has been recognise)
```

U will need to google the setting for your telco. Btw, if u still wanna use this script, pm me and i'll email u the updated one as there are some changes to it.

---

### Post by kdi on 2010-06-14
in Ubuntu 10.04 this become easier. Open System>Administration>Synaptic Package Manager n install usb-modeswitch from there.

Open terminal n type sudo nano /etc/modules hit enter. Add this line:

usbserial vendor=0x1e0e product=0x9100

Save n exit. The next time u boot, this modem is ready to be connected to the internet by clicking the internet connection icon on the right side of the gnome panel.

Enjoy..:popcorn:

Edit - Ok, one would say, how could i install usb-modeswitch since i can't connect my modem to internet in the first place. Don't worry. Here's the solution.
1. Put ur modem in the usb port.
2. Right click the icon appeared on the desktop n choose 'eject'
3. Open terminal n type:

sudo modprobe usbserial vendor=0x1e0e product=0x9100

4. Hit enter n close ur terminal.
5. Click the internet connection icon on the right side of gnome panel n choose 'New broadband connection..." n follow the instruction. Done.

To avoid key-in this command each time u start ur box, just follow my steps of installing usb-modeswitch n adding module in the /etc/modules.

=)

---

### Post by nebileix on 2010-06-14
> **kdi said:**
> in Ubuntu 10.04 this become easier. Open System>Administration>Synaptic Package Manager n install usb-modeswitch from there.

Open terminal n type sudo nano /etc/modules hit enter. Add this line:

usbserial vendor=0x1e0e product=0x9100

Save n exit. The next time u boot, this modem is ready to be connected to the internet by clicking the internet connection icon on the right side of the gnome panel.

Enjoy..:popcorn:

Edit - Ok, one would say, how could i install usb-modeswitch since i can't connect my modem to internet in the first place. Don't worry. Here's the solution.
1. Put ur modem in the usb port.
2. Right click the icon appeared on the desktop n choose 'eject'
3. Open terminal n type:

sudo modprobe usbserial vendor=0x1e0e product=0x9100

4. Hit enter n close ur terminal.
5. Click the internet connection icon on the right side of gnome panel n choose 'New broadband connection..." n follow the instruction. Done.

To avoid key-in this command each time u start ur box, just follow my steps of installing usb-modeswitch n adding module in the /etc/modules.

=)

Yeah. Use his method. My script was done before that. It's easier that way.

---

### Post by Kathees on 2010-07-09
> **nebileix said:**
> Sorry for late reply. For the username and password in the gnome-ppp, will need to depend on ur mobile broadband telco. For my case, my telco dun actually required any username and password. But gnome-ppp would required those field to be filled in. So just input anything in there. If you are using 10.04, you might not need to use the script as from what im aware, the network-manager are able to recognise the device now using modem manager. All you need to do is to eject the device by 

```
$ eject /dev/"sr1"(Replace sr1 with whatever it has been recognise)
```U will need to google the setting for your telco. Btw, if u still wanna use this script, pm me and i'll email u the updated one as there are some changes to it.

Thanks nebilex. I am really sorry for very late reply. After couple of tries I had almost given up on this process and settled with Windows. Last month was very busy since we had some deadlines I couldn't look into the issue anymore.

Last night I tried to run Erlang on my Windows 7 x64 and I couldn't make it.There is just no way to fix and no workarounds I couldn't find. So I wanted to get back to Ubuntu, and the problem arises again and here I'm checking the forum again. I'm at office now so I'll have to look in to the issue tonight.

BTW my network also doesn't require a user name and password. I just need to enter the APN in the very first time to connect. (In Windows)

> **kdi said:**
> in Ubuntu 10.04 this become easier. Open  System>Administration>Synaptic Package Manager n install  usb-modeswitch from there.

Open terminal n type sudo nano /etc/modules hit enter. Add this line:

usbserial vendor=0x1e0e product=0x9100

Save n exit. The next time u boot, this modem is ready to be connected  to the internet by clicking the internet connection icon on the right  side of the gnome panel.

Enjoy..:popcorn:

Edit - Ok, one would say, how could i install usb-modeswitch since i  can't connect my modem to internet in the first place. Don't worry.  Here's the solution.
1. Put ur modem in the usb port.
2. Right click the icon appeared on the desktop n choose 'eject'
3. Open terminal n type:

sudo modprobe usbserial vendor=0x1e0e product=0x9100

4. Hit enter n close ur terminal.
5. Click the internet connection icon on the right side of gnome panel n  choose 'New broadband connection..." n follow the instruction. Done.

To avoid key-in this command each time u start ur box, just follow my  steps of installing usb-modeswitch n adding module in the /etc/modules.

=)

Thanks kdi. When I started to read the reply I was thinking about how do I download the mod switch without the internet but luckily you have given the answer already. :)

Sp tonight I'll try this method and I hope this will work fine.

@nebilex
As you suggested first I'll try this method. If it's didn't work I'll report the problem. May be then I can PM you to sent the script. Advance thanks for helping me ...

---

### Post by kor13ben on 2010-07-12
Hi kdi

I am brandnew to Ubuntu and just installed 10.4 but canot get my Prolink PHS100 3.5G HSDPA working with your method. Is it because I have another model? I just find a "network connection" icon on the top right of the desktop, no "internet connection" and I find nowhere "New broadband connection". How do I "save and exit" a terminal, is "hiting enter" the thind to do?

please give some more explicit advice to a bloody newcommer    kor13ben

---

### Post by pdc on 2010-07-12
kor13ben

some of these devices are recognised as modems and some are seen as CD-ROM storage devices, as all come loaded with software;

maybe if we ask you to type 

> lsusb

in a terminal;

If you get 0x1e0e:0xf000 it is seen as a CD-ROM device;

If you get 0x1e0e:0x9100 it is seen as a modem;

If seen as a modem, 

go half-way down this page to 

Create a mobile broadband connection and follow the instructions:

any joy?

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

---

### Post by kor13ben on 2010-07-12
Hi pdc,

thanks for ur answer

all I get after tiping lsusb is :

   [SIZE=1]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE]
    [SIZE=1]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE]
    [SIZE=1]Bus 005 Device 002: ID 04f3:0230 Elan Microelectronics Corp. [/SIZE]
    [SIZE=1]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE]
    [SIZE=1]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE]
    [SIZE=1]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE]
    [SIZE=1]Bus 002 Device 003: ID 1e0e:f000  [/SIZE]
    [SIZE=1]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE]
    [SIZE=1]Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam[/SIZE]
    [SIZE=1]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=1]The light of the modem is on and mangenta. Trying to open the icon of the modem on the desktop with "autorun" does not work either. Having tiped the line from kdi`s solution does not make any change on the content of "lsusb".[/SIZE]


[SIZE=1]                                              with hope     kor13ben
[/SIZE]
                            

[SIZE=1]
[/SIZE]

[FONT=&quot][/FONT]
  [FONT=&quot][/FONT]

---

### Post by Kathees on 2010-07-14
> **kdi said:**
> in Ubuntu 10.04 this become easier. Open System>Administration>Synaptic Package Manager n install usb-modeswitch from there.

Open terminal n type sudo nano /etc/modules hit enter. Add this line:

usbserial vendor=0x1e0e product=0x9100

Save n exit. The next time u boot, this modem is ready to be connected to the internet by clicking the internet connection icon on the right side of the gnome panel.

Enjoy..:popcorn:

Edit - Ok, one would say, how could i install usb-modeswitch since i can't connect my modem to internet in the first place. Don't worry. Here's the solution.
1. Put ur modem in the usb port.
2. Right click the icon appeared on the desktop n choose 'eject'
3. Open terminal n type:

sudo modprobe usbserial vendor=0x1e0e product=0x9100

4. Hit enter n close ur terminal.
5. Click the internet connection icon on the right side of gnome panel n choose 'New broadband connection..." n follow the instruction. Done.

To avoid key-in this command each time u start ur box, just follow my steps of installing usb-modeswitch n adding module in the /etc/modules.

=)

Hi,

Again another no go. I did exactly like you said. And after exiting from terminal I can see my device listed in the connections and I can see the connection "Airtel Default" listed there. (The name I have given like that and it appeared correctly within Mobile broadband. But when I click that to connect after a little try it's shows me GSM not connected notification.

Strangely after that no longer my Airtel is listed under the connections. Now I think it's again takes as a "Data drive" because in the desktop Prolink icon appears again. 

Now I can do the steps again and it's a cycle ...;)

What is the problem? What should I do now?

---

### Post by kor13ben on 2010-07-14
Hi pdc and everybody else
   
  After playing around fort he first time in my life with a command line I found out that my usb-Modem is recognised by Ubuntu 10.4 as follows :
   
  Modem pluged in, not ejected with a right-click on its icon on the desktop and with dark mangenta LED,   
                           ID 1e0e : f000
   
  Modem pluged in but ejected, LED still dark mangenta,
   
                           ID 1e0e : 9000
   
  After having carried out a second time kdi`s instructions I could see the “Mobile Broadband” on the dropdown menu of the “network connections” but about 30 sec. after trying to connect to it I was informed that I`m offline and there is no connection…
   
  Any suggestions ?              kor13ben

---

### Post by kor13ben on 2010-07-16
Hello again,
   
  i have another problem with Ubuntu10.4 : I managed to establish a connection with a wireless network (signal 100%) but when I try to start Firefox ( for the first time on this OS) it has a problem to load its first page.
  Where should I search to change this frustrating situation. I canot get online because my mobile broadband Prolink refuses to work(see previous posts) and Firefox does not want to connect to an established network connection..
   
  Is anybody out there to offer some help ???       kor13ben
   
  What a shame, I have to send my questions with Windows XP…?!?!?

---

### Post by nebileix on 2010-07-22
Please feel free to pm me. Will try my very best to get back to you guys.

---

### Post by nebileix on 2010-07-22
> **kor13ben said:**
> Hi pdc and everybody else
   
  After playing around fort he first time in my life with a command line I found out that my usb-Modem is recognised by Ubuntu 10.4 as follows :
   
  Modem pluged in, not ejected with a right-click on its icon on the desktop and with dark mangenta LED,   
                           ID 1e0e : f000
   
  Modem pluged in but ejected, LED still dark mangenta,
   
                           ID 1e0e : 9000
   
  After having carried out a second time kdi`s instructions I could see the &#8220;Mobile Broadband&#8221; on the dropdown menu of the &#8220;network connections&#8221; but about 30 sec. after trying to connect to it I was informed that I`m offline and there is no connection&#8230;
   
  Any suggestions ?              kor13ben

Try connecting it again. It might be a bug for now. I experience that as well but didn't really look into it. It work fine again after a few more tries for me thou.

---

### Post by nebileix on 2010-07-22
> **Kathees said:**
> Hi,

Again another no go. I did exactly like you said. And after exiting from terminal I can see my device listed in the connections and I can see the connection "Airtel Default" listed there. (The name I have given like that and it appeared correctly within Mobile broadband. But when I click that to connect after a little try it's shows me GSM not connected notification.

Strangely after that no longer my Airtel is listed under the connections. Now I think it's again takes as a "Data drive" because in the desktop Prolink icon appears again. 

Now I can do the steps again and it's a cycle ...;)

What is the problem? What should I do now?

so sorry for not been around.

lets start with posting the output from the following codes.

```
$ tail -n 100 /var/log/messages
```

Please perform the above code after you tried to connect and the Airtel went missing.

---

### Post by nebileix on 2010-07-22
> **kor13ben said:**
> Hi pdc and everybody else
   
  After playing around fort he first time in my life with a command line I found out that my usb-Modem is recognised by Ubuntu 10.4 as follows :
   
  Modem pluged in, not ejected with a right-click on its icon on the desktop and with dark mangenta LED,   
                           ID 1e0e : f000
   
  Modem pluged in but ejected, LED still dark mangenta,
   
                           ID 1e0e : 9000
   
  After having carried out a second time kdi`s instructions I could see the “Mobile Broadband” on the dropdown menu of the “network connections” but about 30 sec. after trying to connect to it I was informed that I`m offline and there is no connection…
   
  Any suggestions ?              kor13ben

The led for the device should be dark mangenta in color. Btw, have you created the new mobile broadband connection yet?

---

### Post by Kathees on 2010-07-22
> **nebileix said:**
> Please feel free to pm me. Will try my very best to get back to you guys.

Thanks a lot buddy. Since you are ok with it from tomorrow you are going to receive my PMs until I solve this issue.:p

> **nebileix said:**
> so sorry for not been around.

lets start with posting the output from the following codes.

```
$ tail -n 100 /var/log/messages
```

Please perform the above code after you tried to connect and the Airtel went missing.

Ahhhhh! Right now I'm bit of busy since we have to provide the system tomorrow morning. I can't switch to Ubuntu and experiment this right now. It's already 1 in the morning and lot of works to do:(

Please bare with me buddy. I'll try this tomorrow and post the output. May be I'll send a PM right after I posted the output of above code. Thanks in advance for helping out. O:)

---

### Post by Kathees on 2010-07-26
Here is the output of the log you specified :

> 
Jul 26 12:27:08 kathees kernel: [ 9468.945567] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.945574] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.945576] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.945584] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff e0 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.945601] __ratelimit: 11 callbacks suppressed
Jul 26 12:27:08 kathees kernel: [ 9468.946902] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.946910] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.946916] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.946918] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.946925] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff e0 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.948336] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.948344] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.948350] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.948352] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.948359] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fc 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.949774] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.949779] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.949785] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.949787] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.949792] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fc 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.951026] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.951032] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.951038] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.951040] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.951046] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.952510] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.952517] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.952523] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.952525] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.952532] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.954273] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.954279] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.954284] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.954286] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.954292] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.955521] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.955527] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.955532] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.955534] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.955540] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.957148] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.957154] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.957159] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.957161] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.957167] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.959019] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.959025] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.959030] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.959033] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.959038] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.960773] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.960778] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.960783] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.960785] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.960791] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.962991] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.962997] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.963002] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.963004] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.963011] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff f0 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.965655] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.965663] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.965670] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.965672] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.965679] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fc 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.966897] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.966904] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.966910] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.966913] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.966919] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.968403] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.968410] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.968416] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.968418] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.968425] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.972029] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 26 12:27:08 kathees kernel: [ 9468.972037] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 26 12:27:08 kathees kernel: [ 9468.972044] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.972047] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.972054] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 26 12:27:19 kathees kernel: [ 9480.179912] usb 1-5: USB disconnect, address 9
Jul 26 12:27:19 kathees kernel: [ 9480.524517] usb 1-5: new high speed USB device using ehci_hcd and address 10
Jul 26 12:27:19 kathees kernel: [ 9480.661325] usb 1-5: configuration #1 chosen from 1 choice
Jul 26 12:27:19 kathees kernel: [ 9480.668487] usbserial_generic 1-5:1.0: generic converter detected
Jul 26 12:27:19 kathees kernel: [ 9480.668605] usb 1-5: generic converter now attached to ttyUSB0
Jul 26 12:27:19 kathees kernel: [ 9480.668677] usbserial_generic 1-5:1.1: generic converter detected
Jul 26 12:27:19 kathees kernel: [ 9480.668743] usb 1-5: generic converter now attached to ttyUSB1
Jul 26 12:27:19 kathees kernel: [ 9480.686692] scsi7 : SCSI emulation for USB Mass Storage devices
Jul 26 12:27:19 kathees kernel: [ 9480.696156] usbserial_generic 1-5:1.3: generic converter detected
Jul 26 12:27:19 kathees kernel: [ 9480.696271] usb 1-5: generic converter now attached to ttyUSB2
Jul 26 12:27:24 kathees kernel: [ 9485.701166] scsi 7:0:0:0: Direct-Access     PROLINK  MMC Storage      2.31 PQ: 0 ANSI: 2
Jul 26 12:27:24 kathees kernel: [ 9485.704708] sd 7:0:0:0: Attached scsi generic sg3 type 0
Jul 26 12:27:24 kathees kernel: [ 9485.708280] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Jul 26 12:28:10 kathees kernel: [ 9531.425287] usb 1-5: USB disconnect, address 10
Jul 26 12:28:10 kathees kernel: [ 9531.425590] generic ttyUSB0: generic converter now disconnected from ttyUSB0
Jul 26 12:28:10 kathees kernel: [ 9531.425613] usbserial_generic 1-5:1.0: device disconnected
Jul 26 12:28:10 kathees kernel: [ 9531.425768] generic ttyUSB1: generic converter now disconnected from ttyUSB1
Jul 26 12:28:10 kathees kernel: [ 9531.425784] usbserial_generic 1-5:1.1: device disconnected
Jul 26 12:28:10 kathees kernel: [ 9531.441869] generic ttyUSB2: generic converter now disconnected from ttyUSB2
Jul 26 12:28:10 kathees kernel: [ 9531.441893] usbserial_generic 1-5:1.3: device disconnected



1. First I did the steps you mentioned earlier and now my modem is listed in the connections. 
2. Now when I try to connect through that it's says "GSM Disconnected" and now it's vanish form the connections
3. After a minute or so Prolink appears as a data drive again

So what's now? I'm hoping to finish this soon ... :p Thanks in advance ...

---

### Post by nebileix on 2010-07-26
> Jul 26 12:27:08 kathees kernel: [ 9468.966904] sr 6:0:0:0: [sr1] Sense Key : Illegal Request [current]
Jul 26 12:27:08 kathees kernel: [ 9468.966910] Info fld=0x0
Jul 26 12:27:08 kathees kernel: [ 9468.966913] sr 6:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 26 12:27:08 kathees kernel: [ 9468.966919] sr 6:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 26 12:27:08 kathees kernel: [ 9468.968403] sr 6:0:0:0: [sr1] Result: hostbyte=DID_OK 

The above is happening becuz of usb-modeswitch not installed.

Try the following:

1. Remove the phs300 from your system first.

2. Remove usbserial module by
```
sudo rmmod usbserial
```

3. Plug in your phs300 and wait for the led to turn mangenta before you proceed the next step.

4. Eject the device by //your device is recognised as "sr1".
```
eject /dev/sr1
```

5. Load the usbserial module
```
sudo modprobe usbserial vendor=0x1e0e product=0x9100
```

6. Try to connect your Mobile broadband.

Please repeat the steps a few more times if it fail.

Do remember to install usb-modeswitch once you have your connection to the internet.

```
sudo apt-get install usb-modeswitch
```

---

### Post by Kathees on 2010-07-27
> **nebileix said:**
> The above is happening becuz of usb-modeswitch not installed.

Try the following:

1. Remove the phs300 from your system first.

2. Remove usbserial module by
```
sudo rmmod usbserial
```3. Plug in your phs300 and wait for the led to turn mangenta before you proceed the next step.

4. Eject the device by //your device is recognised as "sr1".
```
eject /dev/sr1
```5. Load the usbserial module
```
sudo modprobe usbserial vendor=0x1e0e product=0x9100
```6. Try to connect your Mobile broadband.

Please repeat the steps a few more times if it fail.

Do remember to install usb-modeswitch once you have your connection to the internet.

```
sudo apt-get install usb-modeswitch
```

Hi,
Thank you very much for the response.

I did exactly what you said but still a no go :(

At the first step it says 

> ERROR: Module usbserial does not exist in /proc/modules
 

I tried that couple of times but got the same message again and again. Later I just skipped that step and did the other commands.  It shows the connection there but when clicks it disappears as before. I tried this step like 6 times but no luck.

Here is the log this time : Seems like have the same problem ...

> 
Jul 27 11:07:25 kathees kernel: [ 6482.380705] usb 1-5: generic converter now attached to ttyUSB2
Jul 27 11:07:30 kathees kernel: [ 6487.381269] scsi 14:0:0:0: Direct-Access     PROLINK  MMC Storage      2.31 PQ: 0 ANSI: 2
Jul 27 11:07:30 kathees kernel: [ 6487.384381] sd 14:0:0:0: Attached scsi generic sg3 type 0
Jul 27 11:07:30 kathees kernel: [ 6487.388379] sd 14:0:0:0: [sdc] Attached SCSI removable disk
Jul 27 11:07:31 kathees kernel: [ 6488.705844] usb 1-5: USB disconnect, address 16
Jul 27 11:07:31 kathees kernel: [ 6488.706409] generic ttyUSB0: generic converter now disconnected from ttyUSB0
Jul 27 11:07:31 kathees kernel: [ 6488.706429] usbserial_generic 1-5:1.0: device disconnected
Jul 27 11:07:31 kathees kernel: [ 6488.706583] generic ttyUSB1: generic converter now disconnected from ttyUSB1
Jul 27 11:07:31 kathees kernel: [ 6488.706599] usbserial_generic 1-5:1.1: device disconnected
Jul 27 11:07:31 kathees kernel: [ 6488.724122] generic ttyUSB2: generic converter now disconnected from ttyUSB2
Jul 27 11:07:31 kathees kernel: [ 6488.724152] usbserial_generic 1-5:1.3: device disconnected
Jul 27 11:07:37 kathees kernel: [ 6493.860040] usb 1-5: new high speed USB device using ehci_hcd and address 17
Jul 27 11:07:37 kathees kernel: [ 6493.994992] usb 1-5: configuration #1 chosen from 1 choice
Jul 27 11:07:37 kathees kernel: [ 6494.010056] scsi15 : SCSI emulation for USB Mass Storage devices
Jul 27 11:07:42 kathees kernel: [ 6499.013298] scsi 15:0:0:0: CD-ROM            PROLINK  HSUPA Modem      2.31 PQ: 0 ANSI: 0
Jul 27 11:07:42 kathees kernel: [ 6499.023370] sr1: scsi-1 drive
Jul 27 11:07:42 kathees kernel: [ 6499.023669] sr 15:0:0:0: Attached scsi generic sg3 type 5
Jul 27 11:07:50 kathees kernel: [ 6506.850592] sr: Sense Key : Hardware Error [current] 
Jul 27 11:07:50 kathees kernel: [ 6506.850598] sr: Add. Sense: No additional sense information
Jul 27 11:07:51 kathees kernel: [ 6507.907656] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.907665] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.907672] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.907674] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.907681] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff e0 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.907699] __ratelimit: 6 callbacks suppressed
Jul 27 11:07:51 kathees kernel: [ 6507.909289] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.909296] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.909302] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.909305] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.909311] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff e0 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.910774] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.910780] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.910786] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.910788] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.910794] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fc 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.912162] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.912167] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.912172] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.912175] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.912180] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fc 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.915028] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.915034] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.915039] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.915042] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.915047] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.916280] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.916287] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.916292] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.916294] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.916300] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.918278] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.918284] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.918290] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.918292] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.918298] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.919659] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.919666] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.919671] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.919674] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.919680] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.921028] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.921034] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.921040] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.921042] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.921048] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.922401] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.922406] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.922412] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.922414] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.922419] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.923778] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.923785] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.923790] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.923793] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.923799] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.925152] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.925158] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.925164] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.925166] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.925172] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff f0 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.927037] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.927044] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.927050] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.927052] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.927058] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fc 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.928281] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.928287] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.928293] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.928295] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.928301] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.929934] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.929941] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.929947] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.929949] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.929955] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00
Jul 27 11:07:51 kathees kernel: [ 6507.931149] sr 15:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 27 11:07:51 kathees kernel: [ 6507.931154] sr 15:0:0:0: [sr1] Sense Key : Illegal Request [current] 
Jul 27 11:07:51 kathees kernel: [ 6507.931159] Info fld=0x0
Jul 27 11:07:51 kathees kernel: [ 6507.931161] sr 15:0:0:0: [sr1] Add. Sense: Logical block address out of range
Jul 27 11:07:51 kathees kernel: [ 6507.931167] sr 15:0:0:0: [sr1] CDB: Read(10): 28 00 00 06 ff fe 00 00 02 00


What now? 

And can you tell me a way to manually install that mod switcher with all dependencies? I tried to download it but it shows lot of dependent files .... So how can I download everything? If you can list me all the files I can downloaded from Windows and then install at the Ubuntu.:idea:


Thanks for helping me. :) Waiting for the reply

---

### Post by nebileix on 2010-07-27
> ERROR: Module usbserial does not exist in /proc/modules 

This is fine. It is just telling you that usbserial is not loaded. Cuz Im not sure whether did you follow pbc advise to include usbserial in /etc/modules.

Are you using Lucid release? If yes, unzip the tar file and try the deb file by installing the usb-modeswitch-data first, follow by usb-modeswitch.

Once the installation of the packages is successful, please insert usbserial into /etc/modules as per pbc instruction and do a reboot without pluging in the phs300.

When the system is ready, do ```
tail -f /var/log/messages
``` and plug in the phs300.

You should see a line something like > usb-modeswitch: switching 1e0e:f000 (PROLINK : PROLINK )

Whenever you see this > Jul 27 11:07:31 kathees kernel: [ 6488.706409] generic ttyUSB0: generic converter now disconnected from ttyUSB0
Jul 27 11:07:31 kathees kernel: [ 6488.706429] usbserial_generic 1-5:1.0: device disconnected
Jul 27 11:07:31 kathees kernel: [ 6488.706583] generic ttyUSB1: generic converter now disconnected from ttyUSB1
Jul 27 11:07:31 kathees kernel: [ 6488.706599] usbserial_generic 1-5:1.1: device disconnected
Jul 27 11:07:31 kathees kernel: [ 6488.724122] generic ttyUSB2: generic converter now disconnected from ttyUSB2

it means that the device switch back as a storage again.

Good luck!

---

### Post by rezzafr33 on 2010-10-31
hey guys, i found another workaround, not for phs300 though, mine is phs100.
here what i've done:
1. dont install usb-modemswitch, if it already installed uninstall it or give comment (# sign) or delete the line on /lib/udev/rules.d/40-usb_modemswitch.rules:
```
ATTRS{idVendor}=="1e0e", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'"
```
change it to:
```
#ATTRS{idVendor}=="1e0e", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'"
```
dont forget to reload udev 
```
sudo udevadm control --reload-rules
```
2. Plug your your modem wait until the "virtual/ZeroCD" icon appear.
3. Edit file /etc/udev/rules.d/70-persistent-cd.rules:
```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```
you should see a line similar to this :
```
# HSDPA_Modem (pci-0000:00:10.4-usb-0:7:1.0-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="PROLINK_HSDPA_Modem_1234567890ABCDEF-0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
```
edit it to:
```
# HSDPA_Modem (pci-0000:00:10.4-usb-0:7:1.0-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="PROLINK_HSDPA_Modem_1234567890ABCDEF-0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1", RUN+="/usr/bin/eject %k"
```
save it, then reload udev again:
```
sudo udevadm control --reload-rules
```
4. Unplug your modem, then re-plug it.. now you won't see Prolink's ZeroCD icon, because it automatically ejected and activate the modem, check it with:
```
ls /dev/ttyUSB
```
then dial to internet with your preferred application (i am using kppp or sometimes gnome-ppp)..:guitar:

---

### Post by nebileix on 2010-11-02
gd job rezzafr33... it nice that you share...

Im not sure about PHS100 thou. But for PHS300, it is already a recognise device since lucid. So I dun think anyone would need the script anymore.

anyway, it might assist others..

Cheers...

---

### Post by rezzafr33 on 2010-11-02
> gd job rezzafr33... it nice that you share...
thanks,..  

> Im not sure about PHS100 thou. But for PHS300, it is already a recognise device since lucid. So I dun think anyone would need the script anymore.
i can confirm that PHS100 is already recognized by Lucid (that is why we don't have to call usbserial module with sudo modprobe vendor=0x.... product=0x....), but we need to manually eject the "ZeroCD".

Before we do that it act as a virtual CD, lsusb give following output :
```
...
Bus 001 Device 004: ID 1e0e:f000
...
```
but after we eject it, it act as a modem (and a card reader), lsusb give following output :
```
...
Bus 001 Device 004: ID 1e0e:9000
...
```

to make it simple this workaround skip the step to eject, thats all.. nothing else..
 
Cheers :)

---

### Post by Kevin- on 2010-11-11
:)Thanks kdi !! It worked like a charm !! :guitar:


> **kdi said:**
> in Ubuntu 10.04 this become easier. Open System>Administration>Synaptic Package Manager n install usb-modeswitch from there.

Open terminal n type sudo nano /etc/modules hit enter. Add this line:

usbserial vendor=0x1e0e product=0x9100

Save n exit. The next time u boot, this modem is ready to be connected to the internet by clicking the internet connection icon on the right side of the gnome panel.

Enjoy..:popcorn:

Edit - Ok, one would say, how could i install usb-modeswitch since i can't connect my modem to internet in the first place. Don't worry. Here's the solution.
1. Put ur modem in the usb port.
2. Right click the icon appeared on the desktop n choose 'eject'
3. Open terminal n type:

sudo modprobe usbserial vendor=0x1e0e product=0x9100

4. Hit enter n close ur terminal.
5. Click the internet connection icon on the right side of gnome panel n choose 'New broadband connection..." n follow the instruction. Done.

To avoid key-in this command each time u start ur box, just follow my steps of installing usb-modeswitch n adding module in the /etc/modules.

=)

---

### Post by krish.nagarajan on 2011-03-22
Hello,

I have got the PHS300 fully working in Ubuntu 10.10 (Maverick Meerkat). 

Some things to keep in mind (reiteration of previous posters):


**1) You need to use the modem ONCE in Windows to "activate" it i.e. set the UMTS band etc.** Remember you NEED to do this - you can do it on the PC of a friend. This will also help you confirm the modem, data connection etc is erally working. 

**2) You need the package usb-modeswitch.** This is the best, alternatives like zero_cd might work, but this is the easiest. The latest version (with Ubuntu 10.10) has an out of the box setting for PHS300 in the file :

[FONT="Courier New"][SIZE="2"]/etc/usb_modeswitch.d/1e0e:f000[/SIZE][/FONT]


Install this package by typing the following at a terminal command line:

[FONT="Courier New"][SIZE="2"]sudo apt-get install usb-modeswitch[/SIZE][/FONT] 
(Enter your own password when prompted, then hit Y or enter when prompted). 

3) Once you have rebooted after installing usb-modeswitch (only for good measure, reloading udev etc should also work), insert the modem. 

The light should turn to blue. 

Then, at a terminal cmomand line, load the usbserial module as follows:

[FONT="Courier New"][SIZE="2"]sudo modprobe usbserial vendor=0x1e0e product=0x9100[/SIZE][/FONT]

(Enter your own password when prompted)

After a couple of minutes, a new Mobile Brodband Connection should be visible within Network Manager (the network icon in the Ubuntu bar - at the top / bottom). 


To persist this module load, you can create a file containing the following content and save it (**as root**) as the file [FONT="Courier New"][SIZE="2"]/etc/udev/rules.d/45-prolink-phs300.rules[/SIZE][/FONT]   (**a new file in this directory**) :

[FONT="Courier New"][SIZE="2"]ACTION!="add", GOTO="PHS300_End"

# Is this the actual modem?
SUBSYSTEM=="usb", ATTRS{idProduct}=="0001",
ATTRS{idVendor}=="19d2",
RUN+="/sbin/modprobe usbserial vendor=0x1e0e product=0x9100",
# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"

LABEL="PHS300_End"[/SIZE][/FONT]


Again, upon udev restart or reboot and relpugging the modem in, after a couple of minutes a Mobile Broadband Connection should be visible within Network Manager. 


Best of luck, and do post your experience / I can still help. I have made this modem work in Ubuntu Jaunty, Ubuntu Lucid and Ubuntu Maverick.

I can also give more technical instructions e.g. using gnome-ppp etc. But the above should be the most painless of getting this to work nuder Ubuntu.

---

### Post by ascanio-alba on 2011-05-27
Working as well on Natty 11.04

(after ZeroCD eject or modeswitch and USB device 0x1e0e:9100 appears)

Weird: I have complete UI and system temporary freeze when option.ko/usbserial.ko loads and probing occurs. System always recovers. This happens for about 3-5 secs.

Serial devices: 

using option.ko highspeed serial:

modprobe option
echo "1e0e 9100" > /sys/bus/usb-serial/drivers/option1/new_id

OR
using usbserial.ko module
modprobe usbserial vendor=0x1e0e product=0x9100

The data port is /dev/ttyUSB2; and the monitoring port is /dev/ttyUSB1.
Sometimes modem-manager might probe wrongly and try to use /dev/ttyUSB1
as data port.

udev rule to force MM to use /dev/ttyUSB2 for data (this rule is already in MM git):

/etc/udev/rules.d/77-prolink.rules
# Simtech makes modules that other companies rebrand, like:
#
# A-LINK 3GU
# SCT UM300
#
# Most of these values were scraped from various SimTech-based Windows
# driver .inf files.  *mdm.inf lists the main command ports, while
# *ser.inf lists the aux ports that may be used for PPP.


ACTION!="add|change", GOTO="mm_simtech_port_types_end"
SUBSYSTEM!="tty", GOTO="mm_simtech_port_types_end"

SUBSYSTEMS=="usb", ATTRS{idVendor}=="1e0e", GOTO="mm_alink_vendorcheck"
GOTO="mm_simtech_port_types_end"

LABEL="mm_alink_vendorcheck"
SUBSYSTEMS=="usb", ATTRS{bInterfaceNumber}=="?*", ENV{.MM_USBIFNUM}="$attr{bInterfaceNumber}"

ATTRS{idProduct}=="9100", ENV{.MM_USBIFNUM}=="03", ENV{ID_MM_SIMTECH_PORT_TYPE_MODEM}="1"
ATTRS{idProduct}=="9100", ENV{.MM_USBIFNUM}=="01", ENV{ID_MM_SIMTECH_PORT_TYPE_AUX}="1"
ATTRS{idProduct}=="9100", ENV{ID_MM_SIMTECH_TAGGED}="1"

GOTO="mm_simtech_port_types_end"

LABEL="mm_simtech_port_types_end"

---

### Post by Malsasa on 2012-12-16
Thank you so much for script! Please create more for another modem. And i think you can help more users, especially Windows user migrating, to use Linux more comfort. So many people need help (scripting) like this. 

And you help me. Thank you!

---

