---
title: "dell mini 12 with dellbuntu 8.04 headache"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by loveunit on 2009-04-10
Hi, I'm trying to help a friend fix her PC.. it seems to have a number of problems.. and after speaking to Dell she's asked me to reinstall Ubuntu or put Windows..

The main issue is a lack of CD drive.. so I've spent a good part of today trying to create a bootable USB with Ubuntu 8.10 - I finally got something that seems to be boot.. and have gone into the installation process, however it ends up at a terminal window.. I'm not sure what to ask at that point.

I've done some reading and am currently downloading an .iso image of for the LPIA version of Ubuntu, I've read this might work better, but that it also has more issues..

The PC runs very badly, and at times xserver just dies and then restarts the session.. one of the processors seems to run at 80% all the time.. Dell asked my friend to do some BIOS tests, which they reported as showing no hardware issues..?

My 3.5 year old inspiron 6000 running 8.10 runs twice as well as this brand new PC.. anyone heard something like this before, or got any ideas?

thanks in advance.

---

### Post by tommcd on 2009-04-10
> **loveunit said:**
> 
 I've spent a good part of today trying to create a bootable USB with Ubuntu 8.10 ...

How are creating the usb installer? You can easily create a Ubuntu usb installer from Ubuntu 8.10. See this:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Pasdar on 2009-04-11
It took me two weeks of off and on trying to try and get Windows XP on the ASUS EEE and I still couldn't even though I'm very experienced with computers. The problem with these stupid small laptops is that they don't have optical drives you can put your CD in and that Windows isn't made to be put on a USB stick.
The only programs available for that are third party and suck for the most part (I'm not blaming the programmers).

And with laptops and OSs' being the way they are, if you install anything other than the image you received with your laptop, you are going to have to spend some time installed drivers for your laptop to make it function properly.

The way I solved it was to buy an external DVD writer, I just connected it, inserted the Recovery CD and installed it. As easy as that.

---

### Post by loveunit on 2009-04-11
@tommcd - thanks for the advice, as I have 8.10 installed that's the first thing I tried, however, only after trying it several times, formatting the USB stick and trying other programs such as unetbooting, did it finally work.. ( not sure what triggered it, but it hung first off, perhaps a permissions issue on the stick? ).

anyhow, so I've now got Ubuntu 8.10 on the stick and this goes past the first stages of the installation - I can select a language, then it runs the Ubuntu loading screen, the same as running from the live CD - but it's at that point that I get dropped to a terminal screen... anyone know what i should do then?

I tried to install a few things, like the graphical front to ubuntu, but it tells the latest is already there.. how do I jump from terminal to Ubuntu GUI?

if I restart from terminal it simply reverts to the old installed version -- which is this terrible dell version of 8.04.

thanks in advance.

---

### Post by Pasdar on 2009-04-11
To go from terminal to GUI type **startx**, then it will either start it or it will tell you why its not starting it.

---

### Post by snowpine on 2009-04-11
The LPIA version of Ubuntu is very much a "work in progress" in my opinion. Try the regular i386 version, it should work fine. At least it does on my Mini 9, which I think is pretty much the same hardware as the Mini 12.

---

### Post by loveunit on 2009-04-11
thanks for the command - I've got the following errors:

VESA(0): no valid modes
Screens found, but none have a usable config

Fatal server error:
no screens found
giving up.
xinit: Connection refused ( errno 111 ) unable to connect to xserver
xinit: No such process ( errno 3 ): server error.

then it take me back to the prompt...

what I downloaded is the i386 version - however as this is a dual processor does it need the i686 version?

thanks in advance.

---

### Post by tommcd on 2009-04-11
> **loveunit said:**
> thanks for the command - I've got the following errors:
VESA(0): no valid modes
Screens found, but none have a usable config
Fatal server error: ...

Try booting to recovery mode and run:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then reboot and see if you can get the Ubuntu desktop. See this:
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
> **loveunit said:**
> 
what I downloaded is the i386 version - however as this is a dual processor does it need the i686 version?

The 32 bit (i386)  version is fine. It will work on i686 CPUs.
 There is really no advantage to using the 64 bit version ubless you have 4GB or more of RAM.

---

### Post by loveunit on 2009-04-12
Thanks for the advice, however I'm having serious doubts if xorg configuration is the only issue on this machine.

it seems to stall, and then xserver crashes.. it also has problems running sudo commands, which stop me running basic commands to test hardware.

as I said in the first post, one of the processors is running at 80% all the time.. could a bad install be the cause of this?

it's a "mini" dell, i.e. no CD drive.. so I'm trying to reinstall Ubuntu 8.10 from a USB stick..

to get to the recovery mode, do I need to boot from the USB and change something in the grub loader command?

I guess the commands you suggested will attempt to fix the currently installed version, but perhaps I need to be starting from scratch?

cheers.

---

### Post by tommcd on 2009-04-12
> **loveunit said:**
> 
to get to the recovery mode, do I need to boot from the USB and change something in the grub loader command?

You don't need to boot from a usb stick for recovery mode. When you boot the computer do you see the grub menu? If Ubuntu is the only OS on the machine you may not see the grub menu. If you don't see the grub menu, then hit the **Esc** key as the computer boots. You will get the grub menu. Choose the option to boot to recovery mode.
> **loveunit said:**
> 
I guess the commands you suggested will attempt to fix the currently installed version, but perhaps I need to be starting from scratch?
cheers.
The **dpkg-reconfigure xserver-xorg** will build you a new xorg.conf. This will hopefully fix the "VESA(0): no valid modes..." problem.

> "one of the processors is running at 80% all the time.."

Is the Dell Mini 12 a dual core machine? In any case, using the VESA driver instead of the intel driver that your system probably should use could possibly cause a high CPU usage.

> "it also has problems running sudo commands, which stop me running basic commands to test hardware...."

I'm not sure why you can't sudo. When you get to recovery mode, run this:
```
sudo groups your_user_name
```
This will list the groups your user is a member of. Make sure you are a member of the admin group. If you are not, run:
```
sudo gpasswd -a your_user_name admin
```
Also see this about sudo:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by loveunit on 2009-04-14
Hi, and thanks for the full reply.

my friend decided she'd rather have a badly working OS than let me attempt to fix it ( I did warn her that it was a bit of an experimental fix..! )

and so she took it back and will no doubt be completely frustrated each and every day by how badly it runs.. 

I'm sorry to say, but I believe one potential convert to Ubuntu has been put off by yet another badly built or configured Dell, rushed off the endless production line.. wherever that is..

thanks all for your help.

---

