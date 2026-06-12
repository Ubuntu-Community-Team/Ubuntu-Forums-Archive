---
title: "Mobile Intel 945GM on feisty Howto"
date: 2008-06-09
forum: Hardware
---

### Post by nomad5000 on 2008-06-09
I was having trouble installing my Dell Inspiron 6400 which has a Mobile Intel 945GM Graphics card properly. To be more precise the resolution was not working properly. After hours of search I finaly found out what the problem was. The thing is, that there is already a driver that ships with any major distribution of linux such as Ubuntu. But there is a tiny little problem. It seams, that the screen resolutions that ship with the bios of the card don't have the resolution, you would probably want on a Laptop as a default. Thats why you need a little program, to change this setting to something that might be appropriate for you. In my example this was 1280x800.

Now the first thing you should do is have a normal clean install of Ubuntu.
Next you will need the program we will use to override the default settings from the graphics card. It is called 915resolution. when I wrote this it was available at this link [http://www.geocities.com/stomljen/download.html](http://www.geocities.com/stomljen/download.html)

after downloading the program, you will need to unpack the file.
Probably you will need to do something like

```
tar -xvzf 915resolution-0.5.3.tar.gz
```

where you replace 0.5.3 with the version you downloaded.

this will create a directory called 915resolution-0.5.3 so now you will need to jump into that directory.

```
cd 915resolution-0.5.3
```

once in there, you will want to compile the program which sounds awful but is really simple.

```
make
```

this will do some compiling or maybe even nothing,

now we need to install the program we created.

```
sudo make install
```

now our system is ready to go.

but we still have some configuration to do.

First off, we need to find out what the standard resolution for our system is set to. to do this simply go to the System>Preferences>Screen Resolution menu of gnome. Here you will see some number like 1280x1024 or something similar, write down this nr. 

Now that you know your default resolution, you need to look where exactly on the card this resolution is stored. To do this, just type

```
sudo 915resolution -l
```

you will get a list like:

```

Intel 800/900 Series VBIOS Hack : version 0.5.3

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1280x800, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1280x800, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1280x800, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel


```

search for the line that has the two numbers you wrote down and at the end has the 32 bits/pixel.

In my case this would be Mode 58. What matters is the nr. 58. Write this down somewhere.


Now we are ready to do some testing. open a terminal and type:

```

915resolution 58 1280 800

```

afterwards press ctrl+alt+backspace at the same time, to restart the X server.

if the Xserver restarted in the desired resolution, you have all the information you need.

Now the rest is to tell linux that it should do this command always, before starting your xserver. This is easy.

go to /etc/init.d/

```
cd /etc/init.d/
```


here you will have to edit the file gdm

```
nano gdm
```

right after the line that says:

```
set -e
```

write the command you used earlier (915resolution 58 1280 800)

```

set -e
915resolution 58 1280 800

```

now you should be able to restart your computer and have your desired resolution as default on your system.

So I hope this was of help for those of you with a inspiron 6400.

Everybody have a realy nice day!!!!

Greetings Michael

---

### Post by MockY on 2008-06-10
Ad what is wrong with the following?

```
sudo aptitude install 915resolution
```

Or simply fire up synaptic and check 915resolution and install it?

Your solution is way to much work for nothing since I have never had any issues with this before.

---

### Post by nomad5000 on 2008-06-10
I tried very hard to install 915resolution with apt (Synaptics), but I just can't find that package in the list. So I decided, that maybe other people have the same problem and thats why I wrote this howto. Also, maybe somebody is interested, in what happens behind the scenes when they install 915resolution. Since the install works just fine with you, maybe you can tell me what is wrong with my sources in apt, so that I can find the problem and help people that have a similar situation.

---

