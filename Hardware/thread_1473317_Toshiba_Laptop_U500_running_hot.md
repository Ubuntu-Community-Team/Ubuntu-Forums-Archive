---
title: "Toshiba Laptop U500 running hot"
date: 2010-05-05
forum: Hardware
---

### Post by reef2dive on 2010-05-05
I have a Toshiba Laptop U500 on running 10.04. It runs really hot, with a CPU temp of 88 C according to gkrelm. (Vista runs much colder.)

I do not have any proprietary drivers like special graphics drivers running. When booting 09.10 from stick I have the same issue, so I do not think it is related 10.04 only.

I ran sensor setup which added a parameter to the sensor list. (Sorry I cannot add exactly the command, as I do not want to run the laptop when it is running this hot.)

Is there a possibility to control the fan, so I can switch it on permanently? 
How do I get sufficient information to post a bug?

---

### Post by dino99 on 2010-05-05
sudo pwmconfig : what's the result ?

you may need to install: toshset and toshutils

its a fan acpi issue, try either:

1)
gksudo gedit /etc/default/grub

then replace the line GRUB_CMDLINE_LINUX=""

with GRUB_CMDLINE_LINUX="acpi.power_nocheck=1"

save

exit

then launch sudo update-grub

switch OFF THEN switch ON the laptop

2)
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=\"Linux\""

Save then update-grub

---

### Post by reef2dive on 2010-05-05
Thank you.
:p

The setting
GRUB_CMDLINE_LINUX="acpi.power_nocheck=1" works.
With this command the fan starts at around 65 Celsius

The other setting does not work.
The fan does not start prior to reaching 100 C which is the same behavior as with the setting. At that time the fan only runs for 2 seconds and switches off and the temperature is not controlled.

---

### Post by bj44 on 2010-05-05
Hi All,

I have updated the grub file to slow down the fan on my Toshiba Satellite A70 but none of the commands seems to work.
Here is a copy of my grub (partial) file in Lucia.



# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
# GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=\"Linux\""
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi="Linux""
# GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="acpi.power_nocheck=1"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


 For now I am using   **GRUB_CMDLINE_LINUX="acpi.power_nocheck=1"** which seems to work slightly better than the other commands.

Is there anything else I need to do before overheating and damaging the laptop's CPU? 

Thank You,

---

### Post by reef2dive on 2010-05-07
Honestly I do not know. I am using gkrellm, which you can get through the package manager to check the temperature on the CPUs. According to that the Toshiba U500 is running fine. ;)

---

### Post by dino99 on 2010-05-07
need to experiment and google around (you are not alone )

GRUB_CMDLINE_LINUX="acpi.power_nocheck=0 ?

[http://michaelminn.com/linux/toshiba-u505/](http://michaelminn.com/linux/toshiba-u505/)

[http://art.ubuntuforums.org/showthread.php?t=1420247&highlight=toshiba+U505+fan](http://art.ubuntuforums.org/showthread.php?t=1420247&highlight=toshiba+U505+fan)

---

### Post by bj44 on 2010-05-07
Thanks guys,

I ended up installing Ubuntu 10.04 inside of a Window's directory in order to remedy the noisy fan issue as well as overheating the CPU. I know that is a temporary fix but for now my laptop is running better... 
I'll update as we go forward with this.

---

### Post by mexlinux on 2010-05-10
Please join this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156)

---

### Post by reef2dive on 2010-06-26
An update on this one.
After an upgrade of software, I do not know what happened, the machine started to run hot again. 
I installed the proprietary fglrx driver as I thought that it would be better. Then I found an BIOS upgrade for this Toshiba U500 10L at [http://eu.computers.toshiba-europe.com/innovation/jsp/supportMyProduct.do?service=EU](http://eu.computers.toshiba-europe.com/innovation/jsp/supportMyProduct.do?service=EU) which had been released 17.06.2010 which I installed. (You have to have windows for the BIOS upgrade)
Still no difference. 
After removing fglrx driver and going back to standard, temperature is normal.

---

### Post by itsageo on 2010-07-06
I was having the same problem (m305d laptop running REALLY hot, 80 C)and installed the proprietary driver fglrx 3d graphics driver and it has dropped my temps about 10-15 C.  I know you said you tried it, but perhaps uninstalling and reinstalling it would work too?

---

### Post by reef2dive on 2010-07-08
Hi, thanks for the tip.
I do wonder, as the machine started to get hot after an upgrade through apt. I guess there is a lib file out there that makes it hot. I am using ACPI off, which means, in my understanding that linux is not involved in the temperature control, the BIOS manages it by itself. So I do not understand, how an upper layer SW can block the BIOS from managing. 
I am not using my laptop for that advanced graphics, just Compiz and cube, and I have not noticed any benefit with fglrx driver.

---

### Post by jpds on 2010-07-09
The following commands fixed this issue for me on a Toshiba Satellite U500:

```

$ sudo -i
# echo 0 > /proc/acpi/thermal_zone/TM0/cooling_mode

```

This command sets the cooling mode of the device onto active cooling.

```

# echo 0 > /proc/acpi/fan/FAN0/state

```

Adding these echo statements before the exit 0 in /etc/rc.local made the change permanent.

I have added this to [https://bugs.launchpad.net/bugs/572528](https://bugs.launchpad.net/bugs/572528)

---

### Post by reef2dive on 2010-07-10
Thank you for the tip.
Just a clarification, do you use ACPI off in grub or not, when you use these commands?

---

### Post by jpds on 2010-07-22
> **reef2dive said:**
> Thank you for the tip.
Just a clarification, do you use ACPI off in grub or not, when you use these commands?

I did not make any changes to the ACPI settings in the kernel line.

---

### Post by reef2dive on 2010-08-08
In the setup there is this directory
```
# /proc/acpi/thermal_zone/TZ0$
```
is there any difference between TZ0 and TM0?

When issuing cat
```
# /proc/acpi/thermal_zone/TZ0$ cat cooling_mode 
0 - Active; 1 - Passive

```
I assume that this means it is not activiated as acpi=off is used in grub

When issuing cat
```
# /proc/acpi/fan/FAN0$ cat state
status:                  on

```

What does the 0 represent in ```
# echo 0 > /proc/acpi/fan/FAN0/state
```, on or off?

---

### Post by isachs on 2010-09-16
That worked for me! Thanks so much.

---

### Post by isachs on 2010-09-16
This worked for me, running Toshiba Satellite A305

> **jpds said:**
> The following commands fixed this issue for me on a Toshiba Satellite U500:

```

$ sudo -i
# echo 0 > /proc/acpi/thermal_zone/TM0/cooling_mode

```This command sets the cooling mode of the device onto active cooling.

```

# echo 0 > /proc/acpi/fan/FAN0/state

```Adding these echo statements before the exit 0 in /etc/rc.local made the change permanent.

I have added this to [https://bugs.launchpad.net/bugs/572528](https://bugs.launchpad.net/bugs/572528)

---

### Post by vanoven on 2010-11-05
Hi

i tried to fix the DSDT on the toshiba U500
there was mistakes in fanX status methods so they always return ON

here are the dsdt files, if somebody can try on ubuntu ( i did on debian (i had to recompile kernel) ) 

now fan's levels turn on and off according to their trip points and i can monitor this with yacpi tool

hope it will help

edit: files here [u500-dsdt.zip]("http://vanoven.free.fr/toshiba/u500-dsdt.zip")

---

### Post by reef2dive on 2010-11-07
Thank you. I will try to use them.
(I need to check how to use them first.)
Probably I will have a result in 2 weeks.

---

### Post by Bucky Ball on 2010-11-07
Okay, I am running a brand new Toshiba Satellite Pro L510 and this what worked for me. At boot, edit the kernel line to read:

```
 acpi=copy_dsdt
```*_**NOT**_*:

```
 acpi=off
```If it works, make it permanent in /etc/default/grub.

If you are still having heating issues, check this page:

[http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)

I really wouldn't bother screwing around with anything else; you may just make a mess you need to fix on top of what you have. This is _ALL_ to do with your 'acpi=?' setting one would think. Checking thermal monitors ain't gonna fix anything but will only confirm what you already know: The machine is running too hot.

:)

---

### Post by Ultim8linux on 2010-11-12
> **jpds said:**
> The following commands fixed this issue for me on a Toshiba Satellite U500:

```

$ sudo -i
# echo 0 > /proc/acpi/thermal_zone/TM0/cooling_mode

```This command sets the cooling mode of the device onto active cooling.

```

# echo 0 > /proc/acpi/fan/FAN0/state

```Adding these echo statements before the exit 0 in /etc/rc.local made the change permanent.

I have added this to [https://bugs.launchpad.net/bugs/572528](https://bugs.launchpad.net/bugs/572528)

The first 2 commends resulted in this : -bash: /proc/acpi/thermal_zone/TM0/cooling_mode: No such file or directory

It dint work for me n my U500 is still OVERHEATING

---

### Post by vanoven on 2010-11-12
you should try my DSDT, it works perfectly on my u500, fans behave like they have to, I can now compile kernels and stay at 70° C max

i tried the dsdt on dragonfly BSD too and it works.

the procedure to install custom DSDT depends on ubuntu version
or you can recompile your kernel :p

---

### Post by Bucky Ball on 2010-11-12
Or you can add:

```
acpi=copy_dsdt
```... to /etc/default/grub.

Edit the kernel line at boot to see if it makes any difference and if so make the change permanent in the /etc/default/grub file.

---

### Post by pvt on 2010-11-19
Hi,

I am facing the same issue with a toshiba u500-12d: the fan will only turn on for a few seconds when the cpu gets near 100 degrees. I have tried the following:
[LIST]
[*]acpi.power_nocheck=1 - some improvement: fans work at lower temperatures and the cpu temperature stays below 75 degrees (but only after having put the laptop on standby)
[*] GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=\"Linux\"" - no change
[*] echo 0 > /proc/acpi ... - no change
[/LIST]

Do you have any suggestions?

---

### Post by vanoven on 2010-11-20
Try :

```
acpi=copy_dsdt
```

as said Bucky Ball,
if that doesn't work ( it doesn't work on u500-11D ) 
you can try to use a custom DSDT,  bios file for U500-12D seems the same as U500-11D one so it should works.

DSDT-File : [http://vanoven.free.fr/toshiba/u500-dsdt.zip](http://vanoven.free.fr/toshiba/u500-dsdt.zip)

---

### Post by Juan Camilo Casas on 2010-12-02
Perhaps we won't do all this stuff with the grub.cfg or menu.lst , all we have to do is to install TOSHUTILS and FNFXD from synaptic, it can't be more easy? ;)

---

### Post by reef2dive on 2010-12-04
According to Synaptic TOSHUTILS only work with APM. In my understanding U500 uses ACPI.

---

### Post by vanoven on 2010-12-05
state method of power source for each fans is bogus

```
PowerResource (PF0, 0x00, 0x0000)
        {
            Method (_STA, 0, NotSerialized)
            {
                If (LOr (FSTA, 0x01))
                {
                    Return (One)
                }
                Else
                {
                    Return (Zero)
                }
            }
```

The method _STA always return "One" ( LOr (FSTA, 0x01) is always true )

OS (linux, bsd , other?) checks fan state before turning it on or off. 
So Linux is always trying to turn off fans.

To get the right fans' behaviour you have to change the _STA method.

if you can't load a custom DSDT at boot i can try to integrate it to your kernel if you want.

edit:
[here]("http://vanoven.free.fr/toshiba/linux-image-2.6.35-23-u500_2.6.35-23.41_i386.deb") the kernel 2.6.35-23 #41 for ubuntu 10.10

```
dpkg -i linux-image-2.6.35-23-u500_2.6.35-23.41_i386.deb
```
to install


edit2 : mistake in command line

---

### Post by budo on 2010-12-16
> **vanoven said:**
> 
edit:
[here]("http://vanoven.free.fr/toshiba/linux-image-2.6.35-23-u500_2.6.35-23.41_i386.deb") the kernel 2.6.35-23 #41 for ubuntu 10.10

```
dpkg -i linux-image-2.6.35-23-u500_2.6.35-23.41_i386.deb
```to install


edit2 : mistake in command line

Hi vanoven!
I'm having the same issue with my U500 "Ducati" edition. I tryed everything suggested in this and other pages, without solving the problem.
Finally I decided to install "your" patched kernel with the specific DSDT you provided, but I couldn't install it because I have a 64-bit system...
Is it possibile for you to provide a version compiled for 64-bit? or can you write a little "howto" or provide useful links to compile it by myself?
Thanks!!!

---

### Post by budo on 2010-12-17
> **budo said:**
> Hi vanoven!
I'm having the same issue with my U500 "Ducati" edition. I tryed everything suggested in this and other pages, without solving the problem.
Finally I decided to install "your" patched kernel with the specific DSDT you provided, but I couldn't install it because I have a 64-bit system...
Is it possibile for you to provide a version compiled for 64-bit? or can you write a little "howto" or provide useful links to compile it by myself?
Thanks!!!
OK... finally I recompiled the Kernel, using this guide:
[https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod](https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod)
To integrate a new DSDT I used vanoven ones, and this guide suggested in a txt file in the kernel source itself:
[http://www.lesswatts.org/projects/acpi/overridingDSDT.php](http://www.lesswatts.org/projects/acpi/overridingDSDT.php)
Finally I produced the 64-bit kernel and now the temperature is at about 50° and the fan is active... I expected a lower temperature, but now it works!

---

### Post by eLtOnI0 on 2011-02-08
Hi Budo,

Glad to see someone solved this !

What Toshiba model do you have ? I've got a different one (U500-119), vanoven's table fixes my fan but breaks my Wireless.

Any tip to know what needs to be changed in DSDT table would be welcome ! Thanks

---

### Post by budo on 2011-02-09
> **eLtOnI0 said:**
> Hi Budo,

Glad to see someone solved this !

What Toshiba model do you have ? I've got a different one (U500-119), vanoven's table fixes my fan but breaks my Wireless.

Any tip to know what needs to be changed in DSDT table would be welcome ! Thanks

Unfortunately after an ugrade, the system was broken and I had to  re-install all the stuff... staying "sticked" always to the customized  kernel is not a good thing... we need a faster way to "correct" a new  kernel, keep it aligned with later versions... really a problem for me: I  have to use the laptop for work and I have no time to spend to just  make the fan work correctly! I really hate Toshiba for this!

Now I'm trying to use GIT to be able to fetch all kernel releases and "apply the patch" quickly... 

However...  I used the DSDT provided by vanoven and didn't change anything... it  "almost" worked: I had some issues with the "battery management" which  didn't identify correctly when the supply was connected, when it was "in  charge" and so on... but not always... sometimes it worked... I don't  know if it's a DSDT issue.

The only advice I can give you is to  try to start from the original DSDT of your laptop and correct it... in  previous posts (or other pages I don't remember) someone explained how  to do that... I know: a waste of time just because Toshiba is not able  to create a BIOS that respect the ACPI standards! I have no words but  this: DON'T BUY TOSHIBA ANYMORE! It's plenty of better suppliers out  there!

---

### Post by budo on 2011-02-09
> **budo said:**
> Unfortunately after an ugrade, the system was broken and I had to  re-install all the stuff... staying "sticked" always to the customized  kernel is not a good thing... 

I re-installed the kernel I compiled previously... and the system is broken again. Tryed to check the log: there's a problem with the ATI card... probably the upgraded kernel module (propietary one) is not compatible with the kernel i compiled. I tryed to recompile latest kernel (2.6.35) from Ubuntu (I reached 97° and the fan went on as a protection from BIOS - I think). With the patched DSDT support now it works! Temperature is again at 51°!!!

Now I've learned that, due to the dynamic kernel modules, with a customized kernel it is important to pay attention on any "system" upgrade (not only kernel image/header) since the compiled kernel can be incompatible with some modules...

Perhaps having a PPA on Ubuntu with the latest kernel, sharing all user contributions, could be a good thing... but this only works with satellite u500, it's not a "general toshiba" patch... I've seen a "toshiba_acpi" module in the current kernel but I can't "modprobe" it (No such device) :mad:...

Today I wrote to Toshiba (italy) trying to explain the problem... I know that I'm dreaming about having this problem solved... what a pitty: working with this Satellite and Linux is likely to become a nightmare...

---

### Post by Bucky Ball on 2011-02-09
This might be a bit late but 10.10 has the Toshiba patch (kernel 2.6.35.24). No need to compile your own. Add 'acpi=copy_dsdt' to /etc/default/grub. Worked for me on Toshiba Satellite Pro L510.

---

### Post by eLtOnI0 on 2011-02-10
@Bucky: WOW, seriously !!??

I have to try this asap. Do you still need to recompile your DSDT and load it the initrd, or adding this line to the boot options is enough ?
Did you also have brightness issues on your L510 ? I need to use the setpci command to change it on my U500.

edit: OK I've tried what you proposed, adding this line into the boot options doesn't help


@Budo: I agree with you, recompiling the kernel everytime a new version is released is a real pain. Be sure you do it with YOUR OWN DSDT, and not Vanoven's one, it's way better for compatibility and stability. DSDT tables change from one model to another, and even for the same model ! I've seen a guy on a french forum having the same laptop as mine, but a different DSDT table for the same BIOS version :/

I doubt Toshiba will make a move, especially for their "old" laptop models, they prefer to focus on current ones. It's really sad because I really love their products.

---

### Post by scorpio2002 on 2011-02-12
Hi there, I have a Toshiba Satellite U500-10V. 

If I use acpi=copy_dsdt the fans don't activate and the temperature reaches 90°C. if I use acpi.nopower_check=1 the situation gets better in the sense that at least the fans always work. However, after a while, even if the fans are always on, when I am on youtube, in firefox or running similar things the temperature gets again close to 80-90 °C even if the fans are working!!!

This is incredible. I want to throw away this rubbish laptop, but before I want to see if you can give me some advice. I also tried the dsdt provived here, but the fans never activate with that one :°°°

---

### Post by budo on 2011-02-14
> **scorpio2002 said:**
> Hi there, I have a Toshiba Satellite U500-10V. 

If I use acpi=copy_dsdt the fans don't activate and the temperature reaches 90°C. if I use acpi.nopower_check=1 the situation gets better in the sense that at least the fans always work. However, after a while, even if the fans are always on, when I am on youtube, in firefox or running similar things the temperature gets again close to 80-90 °C even if the fans are working!!!

This is incredible. I want to throw away this rubbish laptop, but before I want to see if you can give me some advice. I also tried the dsdt provived here, but the fans never activate with that one :°°°

This is due to the fact that using nopower_check=1 disables ACPI checks... I think it's the same as disabling ACPI from the BIOS setup. Fans are always on, but not at their full speed... so in certain situation temperature will stay high!

The only way is to have a correct DSDT, recompiling the Kernel... obviusly the best way is to extract and correct your machine DSDT using "iasl"... I used Vonoven fixed DSDT and it worked (just lucky)... Next I'll give a try to the "copy_dsdt" parameter with the standard Kernel...

Meanwhile I wrote an email to Toshiba (Italy) explaining the problem. They answered me Toshiba doesn't support Linux. Really I didn't asked them to support Linux, but to check and fix their DSDT, and release a new BIOS. From my point of view, if Toshiba states that its products are "acpi compliant" they have to be! But this BIOS is not really following ACPI standards as "iasl" reports so many errors!!! It's Toshiba fault! they can't just say "we don't support Linux" since it's not matter of using Linux or not, but of ACPI compliance! I've bought an ACPI enabled device! or not? [-X

---

### Post by scorpio2002 on 2011-02-14
> Meanwhile I wrote an email to Toshiba (Italy) explaining the problem. They answered me Toshiba doesn't support Linux. Really I didn't asked them to support Linux, but to check and fix their DSDT, and release a new BIOS. From my point of view, if Toshiba states that its products are "acpi compliant" they have to be! But this BIOS is not really following ACPI standards as "iasl" reports so many errors!!! It's Toshiba fault! they can't just say "we don't support Linux" since it's not matter of using Linux or not, but of ACPI compliance! I've bought an ACPI enabled device! or not? 

I agree with you, they've lost a customer.

I want to ask one thing: in order to use copy_dsdt do I need a patched kernel or is this option available in the vanilla kernel?!?

---

### Post by Bucky Ball on 2011-02-14
10.10 the Toshiba patch is there and you don't need to recompile your own kernel. Just add 'acpi=copy_dsdt' to /etc/default/grub. Worked for me with Tosh L510. ;)

---

### Post by eLtOnI0 on 2011-02-15
Unfortunately it doesn't on the U500 Bucky Ball  :-?
And scorpio, you don't need a specific patched kernel. Why would you use vanilla's one ?

The only way to make it work (and it works well after this trick) is to correct the error Vanoven pointed at on page 4. Then recompile the kernel.

You can send me your DSDT tables if you need help to compile the kernel. But please don't use Vanoven's one as he doesn't have the same U500 model as yours !

---

### Post by scorpio2002 on 2011-02-16
> The only way to make it work (and it works well after this trick) is to correct the error Vanoven pointed at on page 4. Then recompile the kernel.

Ok, I extracted the dsdt table, fixed it (I have attached a copy, but I think I did it correctly) and compiled a kernel with that DSDT in it. When I boot, I canconfirm that the custon DSDT has been loaded:

```
[    0.000000] ACPI: Override [DSDT-     A00], this is unsafe: tainting kernel
[    0.000000] Disabling lock debugging due to kernel taint
[    0.000000] ACPI: DSDT @ 0xbfd905c0 Table override, replaced with:
[    0.000000] ACPI: DSDT c0a06bac 0C56C (v02 TOSASU      A00 00000001 INTL 20090123)
```


Now, without any special acpi boot option, the fan work.

However, the overheating issue is not solved: the fan work exteremly slowly (sometimes they speed up a bit), but the temperature still reaches 80-88 °C. 

I really don't know what to do. :( May this be connected to the fact that I use the opensource driver for the ATI card?!?

I need to throw away this buggy rubbish... this is not acceptable :(

---

### Post by eLtOnI0 on 2011-08-08
For people still struggling, or interested in running Linux on their Toshiba U500:

[COLOR=DarkRed]**I wanted to let you know that everything is working perfectly on Debian 6 "Squeeze" !!! Brightness, fan, sound and most of the multimedia buttons !**[/COLOR]
You'll have to download the wifi drivers though if you have a Realtek wlan card.

Ubuntu is supposed to be based on Debian, so I wish we could have it working on our favorite (?) distribution soon.

[COLOR=Green]Does someone know where I could notice the developers that Debian did it, so that they could investigate and patch Ubuntu in consequence?[/COLOR]

---

### Post by reef2dive on 2011-08-08
Thank you, I will try that.
I tried Fedora 15, same issue with the heat.

---

### Post by eLtOnI0 on 2011-08-08
Be aware that I have only tried the KDE edition, but it shouldn't change anything.

Please report your experience here :D

---

### Post by M3m3nt0 on 2012-12-18
> **Bucky Ball said:**
> This might be a bit late but 10.10 has the Toshiba patch (kernel 2.6.35.24). No need to compile your own. Add 'acpi=copy_dsdt' to /etc/default/grub. Worked for me on Toshiba Satellite Pro L510.

I'm having the overheating issue on a Satellite Pro U500 and Ubuntu 12.04 x64 ... :(
what exactly do the parameter *acpi=copy_dsdt*?

---

### Post by Bucky Ball on 2012-12-18
[I][B]Thread Closed.

Reason[/B][/I]: Necromancy. Old thread put to bed.

If  you have an issue, please post a new thread with a descriptive title  and as much info as possible in the appropriate forum rather than  attempting to resurrect this dinosaur 40+ posts deep. Thanks.

---

