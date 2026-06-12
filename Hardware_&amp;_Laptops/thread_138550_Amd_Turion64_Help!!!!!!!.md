---
title: "Amd Turion64 Help!!!!!!!"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by fiveeyedbandit on 2006-03-02
I have a Hp special Edition L2000 laptop with an AMD Turion64 procesor, and an ATI radeon Express 200m graphics card. It came with windows xp home on it and I tried to add Ubuntu 5.10 to it and multiboot it with my win xp. I put my windows on a 40gb partition and left the other 40 gb to be used with Ubuntu. After I have downloaded Ubuntu and try to boot it i get an error message that sais "I cannot start the X Server. It is likely the it is not setup correctly. Would you like to view the x server output to diagnose the problem?" then it brings up the standard linux text login. Can any one help me to get this working??????

---

### Post by cronholio on 2006-03-02
What is the output of:

```
grep '(EE)' < /var/log/Xorg.0.log
```

---

### Post by fiveeyedbandit on 2006-03-02
I have already deleated the ubuntu off of my hard drive so I cant answer your question but i was hoping that you could tell me how to set it up durring the reinstall so that this wouldent happen again. 
P.S. It does this with the live cd also.
P.s.s. I deleted the old windows me off of my desktop and installed Ubuntu 5.10 onto it and I can not open the administrator=>network thing to get it to work with my 56k modem.

---

### Post by cronholio on 2006-03-03
> I have already deleated the ubuntu off of my hard drive so I cant answer your question but i was hoping that you could tell me how to set it up durring the reinstall so that this wouldent happen again.

There's no way to tell. You need to know what the reason is before you can fix it. It's not like you can just do something magical during the installation that would prevent all X Server related problems. So the way to go is re-install and check for the error messages first (as described above).

> I can not open the administrator=>network thing to get it to work with my 56k modem.

What happens if you click System->Administration->Networking? Nothing at all?

---

### Post by bato on 2006-03-03
Hi,
try to install again, then from line command do login and digit:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

digit your password

```
sudo vi /etc/X11/xorg.conf
```

if ask again digit your password

you are now in the vi editor. Scroll the page with the arrows and find the Section "Device" it's would be like this (depend of your ati card)

> Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver          "ati"
        BusID           "PCI:1:5:0"
EndSection

add in this section (press ins button to modify the file)

```
Option          "NoAccel"
```

save and exit (press esc then :wq)

now reboot 

> reboot

and cross your finger!

For me it worked
;) 

ps. if you want 3D accelerator you can find a lot of thread about this.

---

### Post by fiveeyedbandit on 2006-03-03
Yes, when i click on System->Administration->Networking, nothing happens. It acts like it is loading it but then nothing comes up.

I am re-installing the ubuntu onto my laptop to find the error message, I am also going to try the method that is said above.

---

### Post by codejunkie on 2006-03-03
[QUOTE=fiveeyedbandit]Yes, when i click on System->Administration->Networking, nothing happens. It acts like it is loading it but then nothing comes up.

I am re-installing the ubuntu onto my laptop to find the error message, I am also going to try the method that is said above.[/QUOTE]
try running ```
sudo network-admin
```in a terminal. if this won't open it try running ```
su
```enter the root password then run ```
network-admin
```

---

### Post by fiveeyedbandit on 2006-03-03
Ok I will try that.

---

### Post by fiveeyedbandit on 2006-03-03
ok, I reinstalled ubuntu 5.10 onto my laptop and tried to do what bato said to do and when i typed in 
       sudo cp /ect/X11/xorg.conf /ect/X11/xorg.cong.backup
it said,
       sudo: unable to lookup ubuntu via gethostbyname()
so I dont know if i typed it in wrong or something but then i tried what cornholio said and i typed in,
       grep '(EE)' < /var/log/Xorg.0.log
and it said,
(EE) Radeon (0): [dri] DRIScreenInit failed. Disabling Dri
(EE) Radeon (0): XAAInit Error
If you could help me fix this it would be much appreciated.

---

### Post by cronholio on 2006-03-03
```
sudo cp /ect/X11/xorg.conf /ect/X11/xorg.cong.backup
```

It's "etc" and "conf".

Then do

```
sudo vi /etc/X11/xorg.conf
```

Or, if you don't know vi, do:

```
sudo nano /etc/X11/xorg.conf
```

Edit the file as described, then save, exit and reboot.

---

### Post by bato on 2006-03-03
mhmm...

the same error on sudo command occours to me when my hosts file corrupted

digit
```

less /etc/hosts
```

it would be something like this

> 127.0.0.1 localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

if it's not, then overwrite with the line above. The first line is important.

---

### Post by fiveeyedbandit on 2006-03-03
YES!!!!
I did what bato said to do, except insted of using the vi editor i used less but it worked the same way and is now running. But I have some new problems on that same laptop. I can not get my AC97 Data Fax Softmodem with SmartCP modem. I have a dialup connection and i cannot get the System-> Administration-> Networking to load. Also I cannot get my Conexant AMC Audio speakers to work either.
Another thing is that when ever i type in any command that starts with SUDO i get the message 
Sudo: unable to lookup Ubuntu viagethostbyname()
I have already tried the host file thing that bato said but it dident fix this.

---

### Post by bato on 2006-03-06
Hi,
I'm happy my instructions work for you too.

About hosts file I forgot to write the computer name....

```
127.0.0.1 localhost.localdomain localhost ErodeLX
```

where ErodeLX is the name of my pc. From your error message you're host name would be Ubuntu.

Try this and let me know if it works :D

---

### Post by fiveeyedbandit on 2006-03-06
thx I'll try that.

---

### Post by bitlooter on 2006-03-13
[QUOTE=bato]Hi,
try to install again, then from line command do login and digit:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

digit your password

```
sudo vi /etc/X11/xorg.conf
```

if ask again digit your password

you are now in the vi editor. Scroll the page with the arrows and find the Section "Device" it's would be like this (depend of your ati card)

add in this section (press ins button to modify the file)

```
Option          "NoAccel"
```

save and exit (press esc then :wq)

now reboot 



and cross your finger!

For me it worked
;) 

ps. if you want 3D accelerator you can find a lot of thread about this.[/QUOTE]

Thanks Bato, your fix work! I hope I didn't messup anything else with that fix.:confused:

---

