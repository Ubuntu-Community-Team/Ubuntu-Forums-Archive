---
title: "Bluetooth and kmobiletools"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by mirshafie on 2006-11-05
I'm trying to connect to my Nokia 7610 with a bluetooth USB dongle (CNet) and kmobiletools. What i need to know is what to set as Mobile phone device, default is /dev/mobile.

The bluetooth dongle and my phone is recognised by Kubuntu. bluetooth:/ in Konqueror says the location of my phone is "/ sdp", but I can't find sdp in /dev, /mnt or /media. Where should i look for it?


By the way, I'm very glad to see bluetooth support comes with Ubuntu. The software that was included with the bluetooth USB took about 15 minutes to install on a P4 Windows XP machine :D

---

### Post by sweemeng on 2006-11-05
first you need to run hcitool scan

then add the address of your phone in /etc/bluetooth/rfcomm.conf

rfcomm0{
device some-bluetooth-address
channel 1;
}
then run:
sudo rfcomm bind rfcomm0

if my case, the bluetooth is in /dev/rfcomm0

so the phone is in there

---

### Post by mirshafie on 2006-11-06
Really cool. I can connect to my phone with KMobileTools now (thanks!), but I still have some problems.

I want to browse and transfer files (pictures mostly), SMS and contacts from my phone to my computer.

KMobileTools finds no SMS or contacts on my phone. How come? I get no error messages. When I click Reload SMS list nothing happens, and when i click Refresh in the Phonebook window I get a progress dialoge that finishes quickly but I get no contacts.

As for files, I believe I need to use OBEX (?). So, when i open OBEX File Transfer for my phone in Konqueror it gives me a blank window. I can transfer files *to* my phone by dropping files there (or with obexftp), but what I want to do is to copy my pictures and some other files to my hdd.

(I guess one way could be to send every single file I want by bluetooth messages with my phone, but for some really strange and unreasonable reason my phone claims that the maximum amount of bluetooth connections are already in use.)

By the way, one thing that works flawlessly is battery status and signal level i KMobileTools :)

Thanks again for your help.

---

### Post by uterrorista on 2007-12-09
> **sweemeng said:**
> first you need to run hcitool scan

then add the address of your phone in /etc/bluetooth/rfcomm.conf

rfcomm0{
device some-bluetooth-address
channel 1;
}
then run:
sudo rfcomm bind rfcomm0

if my case, the bluetooth is in /dev/rfcomm0

so the phone is in there

why /dev/rfcomm0 ???
where can i find where my bluetooth is?

---

### Post by SneakyWho_am_i on 2008-04-08
> **uterrorista said:**
> why /dev/rfcomm0 ???
where can i find where my bluetooth is?


What I've written looks long and difficult, but nah, it's quick and overexplained.



It's not so much a case of finding it as kind of "plugging it in"
I'll share with you what I've got so far. Naturally I assume that you've already installed any packages from Synaptic which you might need (probably you don't need to install any but you most likely at least had a look or you wouldn't be here)
I tried intalling packages before any actual configuring so Ican't tell you if you need any any way but here we go:

First open a terminal. For me it was ALT+F2 and type "konsole" (no quotes)

in the terminal say this:
```
hcitool scan
```
It will give you a list of available bluetooth devices. Here is my output:

```
sneaky@ubuntu:~$ hcitool scan
Scanning ...
        00:18:0F:DE:24:8E       Nokia 6234
        00:10:60:30:3D:08       ubuntu-1
```

As you can see, I have a Nokia 6234 waiting to connect and it's got some kind of ID next to it which looks all sexy like a MAC address or something.
SO

highlight that address, right click it and select "copy"

Next press ALT+F2 and type the following:
```
gksudo gedit /etc/bluetooth/rfcomm.conf
```

gksudo is the graphical version of sudo - we're probably editing a system file so we're doing it as root. If you don't have gedit installed, try kedit, medit, kate etc.
Also instead of gksudo you might have kdesudo, kdesu, or gksu... But no matter, in any event we're editing that file. Its contents should look something like this:
```
#
# RFCOMM configuration file.
#

#rfcomm0 {
#	# Automatically bind the device at startup
#	bind no;
#
#	# Bluetooth address of the device
#	device 11:22:33:44:55:66;
#
#	# RFCOMM channel for the connection
#	channel	1;
#
#	# Description of the connection
#	comment "Example Bluetooth device";
#}
```

That's cool, it's given us (cryptic) instruction of exactly how to do it (albeit in language no human can understand) right there ;)

I edited mine to include the details I'd learned from hcitool. You can probably adjust it to taste, I don't know, but here's what I have right now:

```
#
# RFCOMM configuration file.
#

#rfcomm0 {
#	# Automatically bind the device at startup
#	bind no;
#
#	# Bluetooth address of the device
#	device 11:22:33:44:55:66;
#
#	# RFCOMM channel for the connection
#	channel	1;
#
#	# Description of the connection
#	comment "Example Bluetooth device";
#}
rfcomm0 {
bind yes;
device 00:18:0F:DE:24:8E;
channel 1;
comment "Nokia 6234";
}
```

So I created rfcomm0 right there, made it automatically start (maybe nto a good idea?), specified the address we learned earlier, gave it a channel (whatever that is) and added a device namey commenty thing. I used it as a name, to be honest I don't know what it's for if anything.

Step one: identify device
Step two: add details of device to mysterious file in depths of computer

Now comes step three, basically to flick the switch to turn it on.

If you'd looked for the rfcomm0 file/device earlier, you'd have probably found it to be notably absent, thus:
```
sneaky@ubuntu:~$ ls /dev|grep rf
ptyrf
ttyrf
```

That's what this whole exercise has been about changing. I point it out to you because this is your last chance to check for yourself that it's not there; I like to know what all the commands I'm typing in are doing - probably you do too...

```
sneaky@ubuntu:~$ sudo rfcomm bind rfcomm0
[sudo] password for sneaky:
sneaky@ubuntu:~$ ls /dev|grep rf
ptyrf
rfcomm0
ttyrf
```

As you can see, for the last step I did the rfcomm binding and then checked that the device was present. It was!

So far I've used these tools:
hcitool
ls
grep
sudo
gksudo
konsole
gedit
bash #lol

If you want any information on them, lman them
```
man grep
```
If you're missing any you can probably install them with apt if you like
```
apt-get install konsole
```
which also installs the man page, I think.
ls lists files, grep chops output

Anyway I digress. At this point I tried again in kmobiletools to connect to my phone and nothing happened. grr........
I closed kmobiletools and restarted it. It works! Yay!
Not everything works - I can't send or read SMS... That's not a big hassle though, I will be pleased if I get it but Nokia PC Tools couldn't do it in Windows so hey :)
Everything else seemed to work OK, even the very impressive signal and battery meter things.
I'm stoked actually. Thanks a lot sweemeng

---

