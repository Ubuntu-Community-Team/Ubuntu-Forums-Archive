---
title: "Touchpad not working after update to 12.04 (DELL Latitude E5520)"
date: 2012-05-02
forum: Hardware
---

### Post by guseit on 2012-05-02
Hi.

A couple of days ago, I updated my system from 11.10 to 12.04 LTS. Which, fortunately, solved some X-Session-Crash-Problems. But now I noticed, that I can't use the touchpad anymore.

I'm running Touchpad-Indicator 0.9.1.6 which has the "enable touchpad"-Option disabled. It also does not work when unplugging the USB-mouse like it did running 11.10.
I looked around a little but couldn't find any solution.

Thanks for your help!

cheers
Andy

---

### Post by sds57 on 2012-05-04
same problem with thinkpad t520.
touchpad did not work.
this:
```

# modprobe -r psmouse
# modprobe psmouse proto=imps

```
as root restored touchpad BUT two finger scrolling does not work and "mouse and touchpad" settings panel no longer has the touchpad tab.

---

### Post by guseit on 2012-05-07
Hi.

Thanks, this indeed re-enabled the touchpad! :-)
But now I can't disable it while using an external mouse. :(

cheers
Andy

---

### Post by Sandra121289 on 2012-05-14
Thanks, this also worked for my ASUS UL80VT.
Thought that the problem with the Touchpad was removed after 10.04, but in 12.04 it was not working again.

Was an Elantech Touchpad too.

---

### Post by eveningpolestar on 2012-06-03
> **sds57 said:**
> same problem with thinkpad t520.
touchpad did not work.
this:
```

# modprobe -r psmouse
# modprobe psmouse proto=imps

```as root restored touchpad BUT two finger scrolling does not work and "mouse and touchpad" settings panel no longer has the touchpad tab.

The above code works foy my MSI x620. But once I restart the machine, the touch pad stops working once again and I have to reenter the code. Any solutions??

---

### Post by Shastry1 on 2012-06-30
Hi, I use a Copmaq Presario CQ40 with Ubuntu 12.04LTS in it. I had problems with the touchpad where in, if the external mouse is connected during boot, the touchpad would not work (If the touchpad hardware switch was turned ON the software would switch off and vice versa - in both the cases touchpad would be off). Post #2 got it working minus scroll. Is there any way to reverse it?

---

### Post by trondhuso on 2012-08-23
The modprobe commands also worked on my Dell E4310 after upgrading from 10.04LTS to 12.04.1 LTS.

Maybe something for the devs to look at.

---

### Post by senlim on 2012-08-28
> **eveningpolestar said:**
> The above code works foy my MSI x620. But once I restart the machine, the touch pad stops working once again and I have to reenter the code. Any solutions??

I had the same problem on my Dell Inspiron so added the two commands to the file /etc/rc.local  just before the last line.  not sure if this is the right thing to do but it works.  

the last 4 lines now read:

# By default this script does nothing.
modprobe -r psmouse
modprobe psmouse proto=imps
exit 0

Have re booted a few times and the touch pad works on boot up each time.

---

### Post by Mythek on 2012-09-09
Hey guys theres a mouse and trackpad section in settings. go there click on trackpad and enable the 2finger scrolling or whatever features u feel that you are missing

---

### Post by trondhuso on 2012-09-16
If the trackpad isn't enabled in modprobe, it does not show up in settings. 


Currently my trackpad has become very sensitive, so I am removing the code that I've added to make it work.

---

### Post by trondhuso on 2012-09-16
Check if synaptics-support for xorg is installed..

I ran 
sudo apt-get install xserver-xorg-input-synaptics

and suddenly I the touchpad-tab in mouse-settings was visible.

it's still a bit sensitive, but I am researching.

---

### Post by trondhuso on 2012-09-17
While I am on the Fix-things that does not work like it should - and reporting the findings, I have now fixed the sensitivenes of the touchpad/mouse: 

The sensitivenes was due to Gnome-3-settings for accessability. I turned off 'Trigger click when the pointer hovers' and now touchpad is working like it should.

Trond

---

### Post by ockert8080 on 2012-11-13
I had the touchpad not working.

This worked for me:
1) In ccsm I disabled mouse polling
    This fixed the mouse
2) Disabling mousepolling also disabled desktop-wall, so after disabling mouse polling and you want your desktop-walls back, you need to go back and reneabled mousepolling and also reactivate the desktop-wall. The reactivations did not seem to have any deleterious effects on the touchpad

---

### Post by tagra123 on 2012-11-30
Gateway Netbook  -- was having the same problem. Enabling the touchpad by pressing Function F6 (enable touchpad) during / after bios screen allowed Ubuntu to see the device.

It has only failed once after being dual booted into windows.


Trying the same thing after boot failed.

Wierd!

---

### Post by Nwe Nwe on 2012-12-21
> **sds57 said:**
> same problem with thinkpad t520.
touchpad did not work.
this:
```

# modprobe -r psmouse
# modprobe psmouse proto=imps

```as root restored touchpad BUT two finger scrolling does not work and "mouse and touchpad" settings panel no longer has the touchpad tab.

Hi,
I use Ubuntun 12.10 alongside with Window 7. TouchPad  in Window 7 work well. But, in Ubuntu since instllation complete, it doesn't work. When I type this command "modprobe -r psmouse" in terminal, this following error appear. How to solve it. Please let me know.

Error removing psmouse (/lib/modules/3.5.0-17-generic/kernel/drivers/input/mouse/psmouse.ko): Operation not permitted

---

### Post by lisati on 2012-12-21
> **Nwe Nwe said:**
> Hi,
I use Ubuntun 12.10 alongside with Window 7. TouchPad  in Window 7 work well. But, in Ubuntu since instllation complete, it doesn't work. When I type this command "modprobe -r psmouse" in terminal, this following error appear. How to solve it. Please let me know.

Error removing psmouse (/lib/modules/3.5.0-17-generic/kernel/drivers/input/mouse/psmouse.ko): Operation not permitted

You might need to do this:
```
sudo modprobe -r psmouse
```

---

### Post by rociosiuce on 2012-12-23
Thanks! 
I just used sudo modprobe psmouse and that fixed my problem :)

---

### Post by elvis-nguyen on 2013-01-04
Hi everyone,

I had the same problem when installing Ubuntu 12.04 on Dell Latitude E6530. And I tried to follow [the instructions]("http://resalxh.wordpress.com/2012/09/18/ubuntu-12-04-lts-x64-the-next-step-getting-touchpad-working/"). It absolutely works in my laptop. Why have not you done yet?;)

---

### Post by keniatw on 2013-02-18
> **guseit said:**
> Hi.

Thanks, this indeed re-enabled the touchpad! :-)
But now I can't disable it while using an external mouse. :(

cheers
Andy


I am having this problem now with Ubuntu 12.04. I upgraded from 11.04 on a HP ProBook and the touchpad-indicator was not working properly. My touchpad was permanently disabled. I really hate that thing, but if I don't have a mouse around to use I get stuck!

I used the solution above:

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

and got the same problem: I can't disable it while using an external mouse, and my touchpad became very sensitive.

I'd like to go back on that. Sorry, I am barely a Linux user, so I don't fully understand how it did work  and, of course, how to go back. :)

Any help from you guys that faced this annoying problem for several months?

---

### Post by vigyani on 2013-03-02
Hi
I am using Ubuntu 12.04 on Acer Aspire S3-391. It has been working fine. A few days ago after update touchpad syoped working. I checked dconf-tools seetings for mouse it was fine and nothhing else helped.
Then I installed xserver-xorg-input-synaptics and after the reboot it strted working.

thanks
with regards

---

### Post by sampath4a4 on 2013-06-15
thanks it is working for me, but i need to run these commands every time when i [COLOR=#ff8c00]**reboot my system**[/COLOR]. is there any permanent solution?

---

### Post by ngnmhieu on 2013-06-22
> **sampath4a4 said:**
> thanks it is working for me, but i need to run these commands every time when i [COLOR=#ff8c00]**reboot my system**[/COLOR]. is there any permanent solution?

Put them in a script, and set it autorun at startup. If you don't know how to do it, here some little helps: [http://www.debian-administration.org/article/Making_scripts_run_at_boot_time_with_Debian](http://www.debian-administration.org/article/Making_scripts_run_at_boot_time_with_Debian)

---

