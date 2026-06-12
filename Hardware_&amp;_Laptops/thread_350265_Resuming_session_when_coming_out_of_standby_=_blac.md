---
title: "Resuming session when coming out of standby = black screen?"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by BoyBlunder on 2007-01-31
hi all.

I'm having some issues with getting my ubuntu install to go into standby mode on my laptop. it's a dell m1210, with a 7400go card (nvidia) and whenever I try to resume my session after going into standby, my screen goes totally black and I'm unable to do anything until I hard reset it. any ideas?

---

### Post by Paerez on 2007-01-31
Run the command:
```
gksudo "gedit /etc/default/acpi-support"
```
The edit these lines:
```
# change this to false
SAVE_VBE_STATE=false

#change to true
DOUBLE_CONSOLE_SWITCH=true

# change to true
USE_DPMS=true

```

Experiment with those three settings, flipping them to true/false. See what happens.
USE_DPMS=true

---

### Post by BoyBlunder on 2007-01-31
no luck after trying all 9 different combinations :(

---

### Post by BoyBlunder on 2007-01-31
i got it working with the following script
```


#!/bin/bash
# /etc/acpi/suspend.d/25-beryl-suspend.sh

pids=""
for pid in `pidof /usr/bin/beryl-manager`
do
ps -o comm= --ppid $pid | grep -q '^beryl$'
if (($? == 0)); then
pids="$pid $pids"
kill -USR2 $pid
fi
done
export BERYLMGRPIDS="$pids"

#!/bin/bash
# /etc/acpi/resume.d/99-beryl-resume.sh

for pid in $BERYLMGRPIDS
do
(sleep 10 && kill -USR2 $pid)&
done
```

---

### Post by dimeotane on 2007-02-05
With this script.. when do I run it, or is it a 'patch' that will fix the problem after being run once?

---

### Post by Evi1d33d on 2007-02-08
Which file do you add the script in?

---

### Post by BoyBlunder on 2007-02-08
they are 2 different scripts.

this one goes in /etc/acpi/suspend.d/25-beryl-suspend.sh
```
#!/bin/bash
# /etc/acpi/suspend.d/25-beryl-suspend.sh

pids=""
for pid in `pidof /usr/bin/beryl-manager`
do
ps -o comm= --ppid $pid | grep -q '^beryl$'
if (($? == 0)); then
pids="$pid $pids"
kill -USR2 $pid
fi
done
export BERYLMGRPIDS="$pids"

```

and this one goes into /etc/acpi/resume.d/99-beryl-resume.sh
```

#!/bin/bash
# /etc/acpi/resume.d/99-beryl-resume.sh

for pid in $BERYLMGRPIDS
do
(sleep 10 && kill -USR2 $pid)&
done
```

---

### Post by Evi1d33d on 2007-02-08
No luck :( The same black screen comes up with I tried to resume my session. Maybe it's because I'm using a desktop not a laptop.

---

### Post by dimeotane on 2007-02-14
Boyblunder... .. Thankyou thankyou thankyou thankyou!!!!!!!!!
 Y O U  R O C K 
:guitar: 

Putting that script in, now my XPS m1210 laptop actually goes into standby properly.  All the blue lights shut off, and the power symbol 'pulses', while in standby.   It actually comes out of stand by properly now!

I honestly thought my beeeautiful m1210 was destined to be without standby, and was considering trying to remove beryl and every update until I could get it to work again.
Dare I ask how you figured out how to make that script.  This is what makes Ubuntu so great, the wonderful support community of genius hackers.

---

### Post by DavidFourer on 2007-02-14
Boyblunder's scripts are over my head.  After upgrading to Edgy, the sleep didn't wake up.  I rebooted with kernel 2.6.15-27-686 instead of -17-11-generic or any of the other -17-??-???.  This worked so I edited /boot/grub/menu.lst.

That might be a crude way to fix this but in all other respects I'm running Edgy Eft on my notebook computer and it seems fine.  Eventually I might have to get -17- working--huh?.  I could create/edit the files as described and see what happens.  When I have no idea the logic of it, something usually hangs.  Or maybe upgrade 7.06 will come out and work out of the box, like Dapper.

Perhaps someone will offer some comment here.  I suppose i could look up the man page for every line in the script and see what new things I can learn.

---

### Post by PRGUY85 on 2007-02-16
The script works for me, yet not entirely. When I come back from standby I get the password field to enter the desktop again.  Yet, I cannot type on the field, just click the buttons (unlock, switch user...)...Also if I do CTRL ALT cursor keys I get the moving cube from Beryl which makes it seem as if it is a program running on the regular desktop instead of something built to the desktop itself.  

If I can get a way to type on that box, then it all works out.  Yet, for now it doesnt... I will have to keep switching to metacity everytime I standby.

---

### Post by dimeotane on 2007-03-06
:confused: 

I'm guessing that since I did a update (a beryl update?) the script I entered appears not to work any longer.

I'm going to try re-entering it, but I hope I won't lose my sleep functions every time I update beryl!  Hopefully we can find a long term fix soon?

---

### Post by medomedo on 2007-03-18
I am using beryl version "0.2.0~0beryl1". The script provided by BoyBlunder works partially. meaning that before using his script, I had to ctrl+alt+F1 then back ctrl+alt+F7 to get my X session. After using his script, I need to flip the cube to get my session. One flip can do the trick.
We still need to improve the script little bit more.

Thanks BoyBlunder. keep the good work.

---

### Post by martinw89 on 2007-03-23
I was having the same problem, it seems like it's [a bug]("http://bugs.beryl-project.org/ticket/1513") in either Beryl or the NVIDIA drivers.  A combination of changing ACPI options and NVIDIA driver settings seemed to work for me, but I also uninstalled Beryl soon afterwards and I can't say how consistent that method was.

---

### Post by martinw89 on 2007-03-28
Hi again guys.
It seems that changing rendering platform to "Force AIGLX" has gone around this bug for me, with no noticeable performance difference.  However I'm using Feisty and there are many things that could also contribute to this setting working, Feisty uses a newer X for example.  Can anyone else confirm this workaround?

---

### Post by trybik on 2007-04-02
> **PRGUY85 said:**
> The script works for me, yet not entirely.

I used different script  (the one from beryl site: [http://forum.beryl-project.org/viewtopic.php?f=39&t=789&p=5583#p5583]("http://forum.beryl-project.org/viewtopic.php?f=39&t=789&p=5583#p5583")), but still:

> **PRGUY85 said:**
>  When I come back from standby I get the password field to enter the desktop again.  Yet, I cannot type on the field, just click the buttons (unlock, switch user...)...Also if I do CTRL ALT cursor keys I get the moving cube from Beryl which makes it seem as if it is a program running on the regular desktop instead of something built to the desktop itself. 

got the same bug. Couldn't find the solution so I've edited
```
sudo gedit /etc/default/acpi-support
```
and commented out
```
# Comment this out to disable screen locking on resume
LOCK_SCREEN=true
```
Not something good for your notebook security but at least this bug is temporarily out. Anyway looks like suspend still depends on system humor. If anyone knows how to get rid of 'unable to type in the password box' problem after suspend please let me know.

Greetz,
Mikolaj

---

### Post by martinw89 on 2007-04-02
Hi trybik,
Just out of curiosity, have you tried forcing AIGLX like I mentioned in my last post?  I'm curious if this is something unique for my box or if it works all around.

---

### Post by trybik on 2007-04-02
> **martinw89 said:**
> Hi trybik,
Just out of curiosity, have you tried forcing AIGLX like I mentioned in my last post?  I'm curious if this is something unique for my box or if it works all around.

Hi!

Nope, I've been using Beryl with AIGLX anyway.

Greetz.

PS. I've finally reached the point at which voice of reason told me to stop waisting time on trying to get another 'almost working' feature in Beryl/Compiz actually work. That feels so gooood.

---

### Post by martinw89 on 2007-04-02
Yeah I'm actually not using a composite window manager at the moment either.  I thought my Beryl was using AIGLX also but it actually defaulted to NVIDIA's implementation.  Forcing non-NVIDIA AIGLX seemed to do the trick for me.

---

### Post by neopran on 2007-04-02
Thanks a lot man, this actually worked for my Acer Aspire 5672 on Edgy.

Cheers:D



> **BoyBlunder said:**
> they are 2 different scripts.

this one goes in /etc/acpi/suspend.d/25-beryl-suspend.sh
```
#!/bin/bash
# /etc/acpi/suspend.d/25-beryl-suspend.sh

pids=""
for pid in `pidof /usr/bin/beryl-manager`
do
ps -o comm= --ppid $pid | grep -q '^beryl$'
if (($? == 0)); then
pids="$pid $pids"
kill -USR2 $pid
fi
done
export BERYLMGRPIDS="$pids"

```

and this one goes into /etc/acpi/resume.d/99-beryl-resume.sh
```

#!/bin/bash
# /etc/acpi/resume.d/99-beryl-resume.sh

for pid in $BERYLMGRPIDS
do
(sleep 10 && kill -USR2 $pid)&
done
```

---

### Post by csthiang on 2007-07-31
> **neopran said:**
> Thanks a lot man, this actually worked for my Acer Aspire 5672 on Edgy.

Cheers:D

Does not work for my Acer 3282.

Is it because I am using compiz?

---

### Post by aldeby on 2007-09-11
I had this experiece with gutsy gibbon (tribe6):

**Problem:** Black screen when resuming from suspends

However /etc/acpi/prepare.sh file has no issues

**Cause:** **compiz! **(to figure out do a simple test: disable compiz before entering standby and you should be perfectly able to resume)

**Solution:** install via apt-get [B]CompizConfig
[/B]then in **General Options** go to **Display Settings **and disable **Sync to VBlank**


If problem persists also try changing some values in /etc/default/acpi-support

most notable change should be changing POST_VIDEO=true to POST_VIDEO=false

hope it helps,
cheers :)

---

### Post by ionman on 2007-10-12
> **aldeby said:**
> I had this experiece with gutsy gibbon (tribe6):

**Problem:** Black screen when resuming from suspends

However /etc/acpi/prepare.sh file has no issues

**Cause:** **compiz! **(to figure out do a simple test: disable compiz before entering standby and you should be perfectly able to resume)

**Solution:** install via apt-get [B]CompizConfig
[/B]then in **General Options** go to **Display Settings **and disable **Sync to VBlank**


If problem persists also try changing some values in /etc/default/acpi-support

most notable change should be changing POST_VIDEO=true to POST_VIDEO=false

hope it helps,
cheers :)

THANK YOU SO MUCH! Changing POST_VIDEO to false worked!

---

### Post by climatewarrior on 2007-10-13
Worked perfectly on my laptop. I have a Latitude X300 and im gutsy release candidate.THis is my video card. 855GM intel integrated graphics card.

Thankyou!

(Actually it only worked for the first time, now im back to sqaure one, I also found out that my suspend works well without compiz so it has to be something related to that)

---

### Post by Zoroaster2 on 2007-10-24
Yeah I tried all those things and more and none of it worked.  I still get a black screen most of the time and sometimes I get an all bright green screen.  Any other ideas anyone?

---

### Post by rhemal on 2007-11-20
thanks all for this thread. the POST_VIDEO option set to false was what did the trick for me.
I have a Dell D620 with Nvidia GFX

---

### Post by user17 on 2008-01-02
After much fretting and reading no end of bloggery on Gutsy's inability to wake up, I changed **POST_VIDEO=true** to **POST_VIDEO=false**, and now everything works perfectly! :) This is on a Compaq Presario V5206. Thank you!

---

### Post by kaston on 2008-01-04
> **aldeby said:**
> I had this experiece with gutsy gibbon (tribe6):

**Problem:** Black screen when resuming from suspends

However /etc/acpi/prepare.sh file has no issues

**Cause:** **compiz! **(to figure out do a simple test: disable compiz before entering standby and you should be perfectly able to resume)

**Solution:** install via apt-get [B]CompizConfig
[/B]then in **General Options** go to **Display Settings **and disable **Sync to VBlank**


If problem persists also try changing some values in /etc/default/acpi-support

most notable change should be changing POST_VIDEO=true to POST_VIDEO=false

hope it helps,
cheers :)i apologize in advance for my total noobness.

i have a toshiba satellite A100 VA9 with an NVIDIA Geforce 7 series graphics card (at least that's what it said in system->administration->screens and graphics.  in my power management preferences, under actions i have when laptop lid is closed:  blank screen and put display to sleep when inactive for 20 min.  after the display has gone to "sleep" i seem to have the same problem as most where the screen doesn't wake up.  this sleep is different than suspend and hibernate, because in sleep the power light does not pulse like it does in suspend and hibernate.  however, i also have the same problem with both suspend and hibernate so i just stopped using those altogether.  

it looks like the post that i've quoted has helped a lot of people, might this also be my solution?  if so i'd like to try it but i need some help.  i think i've found out what compiz is but i don't know how to disable it to test if it is the problem and i don't know how to get to "general options" as stated in the post.

any help would be appreciated!  thanks!

---

### Post by madscientist032 on 2008-01-06
where is the alleged POST_VIDEO that I need to change? Is it in the Compiz Advanced Settings Manager or do I need to do something else?

---

### Post by mrfuzzemz on 2008-01-06
> **madscientist032 said:**
> where is the alleged POST_VIDEO that I need to change? Is it in the Compiz Advanced Settings Manager or do I need to do something else?


You'll find the option in /etc/default/acpi-support

Edit it with gedit or nano like this:

```
sudo gedit /etc/default/acpi-support
```

---

### Post by High_Yield on 2008-01-14
I have the same issue with a desktop and an old GeForce Mx440 video card.

All works fine with normal computing, games(Open Arena) etc...

Then I go to standby, which "appears" to work properly - good.

Later I try to resume and a see lights blink - hear the PC "whirrr" back up, but then only a black screen - nothing more.

Have tinkered arund with the BIOS settings (S1, S3), have turned compiz off, have tinkered with the aforementioned file and VBE/POST options - all to no avail.

I have a desktop with a K7 Triton 400 motherboard (GA-7VA...) with an Athlon XP 1700+ CPU and a GeForce Mx440 vid card.  Other than the "resume" issue and a NAGGING issue with Samba (both Gedit and Nautilus), I really like ubuntu.

Any "black screen" thoughts are welcome - or let me know what "settings file" or "log file" to post if will help debug things.

Regards - B

---

### Post by tinklybear on 2008-05-26
post_video=false worked for me too! Compaq f572us laptop

---

### Post by sgardne on 2008-06-08
Hi everyone. I am running an Asus P5WD2 Intel board & Nvidia GeForce 7 gfx card tower with Ubuntu x86_64. I always get the black screen after returning from standby. I've tried turning off compiz, along with every other suggestion in this forum, to no avail.

I actually managed to upgrade my Nvidia drivers to the latest version after much hassle, which did not fix the problem. The last kernel upgrade totally broke that, so I ended up reinstalling Ubuntu rather than trying to futz with the drivers again (god, there's got to be an easier way). Anyway, after the reinstall, now I have a new development: when I resume from standby I get a continuously repeating system beep. Beepbeepbeepbeepbeepbeepbeepbeepbeepbeepbeepbeepbeepbeepbeepbeep until I hit the reset button. 

I'm at a loss here. I really want standby to work. I've been fighting with this for a week. I feel like I have pretty standard hardware here, maybe I'm just overlooking something simple?

---

### Post by vprasaj on 2008-06-11
I have just solved my problem. The same thing.

O.K. I have AGP card (nvidia 6600gt). I added in /etc/X11/xorg.conf in section "Device"

```
Option "NvAGP"  "1"
```


Now it looks like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option "NvAGP"  "1" 
EndSection
```

Then I edited  /etc/default/acpi-support
and changed
```
POST_VIDEO=true
```
to
```
POST_VIDEO=false
```

Rebooted and tested.

Now I can suspend and hibernate.\\:D/[-o<

This was my problem... (for 3 years #-o)

I hope this helps to someone...

Edit:
If I use compiz, then it resumes with white blank screen. But i just type password (blindly), and everything is back.

---

### Post by sgardne on 2008-06-11
Awesome, I will give this a try as soon as I get home!

---

### Post by sgardne on 2008-06-12
I realized when I got home that this was probably only applicable to folks with AGP cards. Mine's a PCI-E. So, I didn't try it. I think I might try installing Debian Etch and see if that makes it happen for me.

---

### Post by mbw163 on 2008-06-20
My lappy now wont even go to standby when i chagned the post_video to false. same when i chagned it back to true

Sony vaio sz430

---

### Post by bebops_lost on 2008-06-25
I can't download CompizConfig:
I do this
```
sudo apt-get install CompizConfig
```
and get:
E:Couldn't find package compizconfig.

I'm using Hardy, so maybe I don't have the same download options, but I have a nVidia Geforce 6150 on an HP 1100 laptop... also I can't find the 
"General Options > Display Settings > disable Sync to VBlank" path... anybody have any ideas?

---

### Post by pall.e on 2008-07-06
Hey all, 
I have a Asus U6, and changing post-video worked and then I in installed Emerald and it no longer worked.  I tried uninstalling Emerald but now it won't work again.  Anyone know how to either fix this or completely get rid of Emerald (I did apt-get purge and it didn't seem to change back whatever settings I broke.)
Pall

---

