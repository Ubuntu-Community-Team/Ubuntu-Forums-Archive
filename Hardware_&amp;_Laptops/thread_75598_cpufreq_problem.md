---
title: "cpufreq problem"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by wygenius on 2005-10-13
I got the following error when im trying to install ubuntu 5.10 on my Dell Inspiron 8100:
cpufreq:change failed with new_state 1 and result 0
Is it because the Speedstep technology? How do i solve it?
Thank you!:razz:

---

### Post by dbloom on 2005-10-20
i have the same issue after upgrading to kubuntu breezy (same Dell Inspiron 8100).  though it only happens while shutting down....

it doesn't seem to affect anything, but i'm curious what's going on -- never saw this before.

---

### Post by mjwood0 on 2005-10-21
Another Dell Inspiron 8100 user here with this problem.

What module should be loaded for this???  

Anyone with more info?

---

### Post by mjwood0 on 2005-10-21
Submitted a bug to bugzilla #18213

The incorrect speedstep module is being loaded.

To fix this, edit /usr/share/powernowd/cpufreq-detect.sh so it reads like this:

```

# Two modules for PIII-M depending the chipset.
# modprobe speedstep-ich$EXT || modprobe speestep-smi$EXT  would be another way
if [ -f $IOPORTS ] && grep -q 'Intel .*ICH' $IOPORTS ; then
  PIII_MODULE=speedstep-ich
else
#  PIII_MODULE=speedstep-smi
  PIII_MODULE=speedstep_ich
fi

```

Let me know if this helps.

edit: You'll probably have to reboot for it to work.

---

### Post by tommy297 on 2006-01-04
Hi,
this trick helps on my Latitude C600. Thank you very much. Processor is Coppermine (PIII) 750/600MHz.
cu
tommy

---

### Post by brain.g on 2006-02-09
Just another confirmation ...  This edit also worked for me on a Dell Latitude C600.

---

### Post by lostwong on 2006-03-09
I just installed Breezy on a Dell Inspiron 8100 and your fix seems to be working great.  Thanks for contributing!

---

### Post by lazerdave on 2006-03-16
I was having a similar problem on my Inspiron 8100, and found that removing powernowd corrected the problem instantly.

Aside from getting the same message at shutdown, I was having frequent mouse freezes (for about 1/2 second) and audio-looping as pages were loading.  Looking at the system monitor, I would see that my CPU usage was frequently spiking to 100% and staying pegged there for a few seconds.

Now I'm rarely going over 80% and everything seems to be ok.  Hopefully I'm not doing any damage to my CPU by (presumably) having it run at full clock speed all the time and not throttling down.

Thoughts?

---

### Post by siennalizard on 2006-03-19
Just wondering if this sounds like a similar powernowd problem: My powernowd seems to be loading the speedstep-centrino module, but, even when powered, the laptop won't run faster than 1.2GHz, though it's a 2GHz chip.

J.

---

### Post by mufflon on 2006-07-03
[QUOTE=mjwood0]Submitted a bug to bugzilla #18213

The incorrect speedstep module is being loaded.

[SNIP]

Let me know if this helps.

edit: You'll probably have to reboot for it to work.[/QUOTE]

FYI: Same problem occured on a Dell Latitude C810 with BIOS A12.
Your solution worked like a charm! :D
Thanks!

---

### Post by shizeon on 2006-11-06
Worked for me also in Edgy on a Dell Latitude CPx.  Thanks for posting!

---

### Post by ryanov on 2006-11-06
Hate to be the bearer of bad news, but why this "works" is because a Dell Inspiron 8100 will not load the ICH module. Go ahead, try it and reboot -- you'll see you now have NO speedstep module, and that is why you don't see the constant freezes.

Myself, I'd be fine with the freezes if the speedstep could be made to work the way it does in Windows -- slow on battery, fast on power. But... I can't figure that out as-yet.

---

### Post by nea on 2006-11-11
I've a Dell c810 (p3_1133), and everything it's ok, until I install edgy! :confused: 
Now the modify "PIII_MODULE=speedstep_ich" cause the fix of freq at max (always 1133).
Obviously with -smi I've 1-2 second of freeze any time the freq goes down.

Can anyone explain me why?:-k

---

### Post by nea on 2006-11-11
I boys... I understand...
The problem is that the module speedstep_ich is assent in i386 kernel, if you use the generic kernel, edgy goes right!!!

If you want to use the i386 kernel you mast:
1. attend the bugfix
2. re-compile the kernel

Bye NEA

---

### Post by benjo316 on 2007-07-08
I know this is an old post, but it seems like it is again a problem in 7.04 (Feisty) and I believe I have a solution.

If you would like to look at the bug report it is [here]("https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/24353").

I'll just summarize it here:

1.) Go to this [link]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#CPU").
2.) Follow the instructions under ' How to enable your CPU's Power Saving/Frequency Scaling features', except removing user space scaling software(Step 2) is probably unnecessary if you edit the script used to choose what method to scale the processor. You can also skip the identification of your CPU, because if you're here you are probably using the same laptop as me(inspiron 8100 or similar) and most likely have the same processor(Pentium III [M?], for which a supported module isn't listed).

3.) If you do in fact have the same processor as I do, then proceed to install the module for 'Others (Unknown)' and then go on to step 4.
4.) You may then follow the rest of the guide in order to get it working correctly. ^.^

Please post your results here and if you know how to do this without removing the user space scaling software please provide that information as well, since doing so forces you to remove the 'ubuntu-desktop' meta-package as well. Also, please contribute to the bug report as well. ;)

The results for me seemed proving to me that it is a working solution. According to the scaling applet it is scaling correctly and I'm not getting any 'cpufreq' errors anymore. My laptop also runs a lot cooler when idle.

Hope that helps. ^.^

---

### Post by phonky on 2007-07-08
Hi benjo

when I try 'sudo modprobe acpi-cpufreq' I get
an error message, like FATAL: error....: device busy

I can follow the other steps (installing the utils, etc.), but I can't set the governor.
Unfortunately, I only get a general error message, saying if
I am root (which I am), if I mistyped the governor (which I didn't), etc.

I have an Inspiron 8100, so I have the same CPU you have. I still have that problem....

lsmod says I have loaded speedstep_smi

do you have any other hint?

thanx
fabio

---

### Post by benjo316 on 2007-07-08
> **phonky said:**
> Hi benjo

when I try 'sudo modprobe acpi-cpufreq' I get
an error message, like FATAL: error....: device busy

I can follow the other steps (installing the utils, etc.), but I can't set the governor.
Unfortunately, I only get a general error message, saying if
I am root (which I am), if I mistyped the governor (which I didn't), etc.

I have an Inspiron 8100, so I have the same CPU you have. I still have that problem....

lsmod says I have loaded speedstep_smi

do you have any other hint?

thanx
fabio

Yeah, sorry about that. I forgot about it. You have to do ```
sudo modprobe -r speedstep-smi
``` to unload the speedstep-smi module before you can load the acpi-cpufreq module.

Thanks for reminding me. ^.^

---

### Post by phonky on 2007-07-08
OK, I did
'modprobe -r acpi-cpufreq', this worked fine.

But I still can't do
'sudo cpufreq-set -g ondemand'

I get
Error setting new values. Common errors:

and then it goes asking if I have admin rights (I have),
if the policiy is modprobed (yes), if the policy exists (yes),
blabla

any more ideas?

But hey, I think the messages of the cpufreq failing are gone!
thanks
fabio

---

### Post by benjo316 on 2007-07-08
Okay, I'll go step by step to make it easier to follow. ^.^
Make sure you are following exactly or it won't work. If you get any errors you should stop and see what happened so that you or someone else can fix it.

1.)```
sudo modprobe -r speedstep-smi
```

After that you shouldn't have any modules loaded currently that handle stepping. You shouldn't be getting any more errors or be able to change the speed governor.

2.)```
sudo modprobe acpi-cpufreq
```(If this doesn't work then go back to step one and try again. If it still doesn't work post what you did and me or someone else will try to help)
This will load the module that you need.

3.)Load the other modules which depend on that module:```
sudo modprobe cpufreq_conservative
sudo modprobe cpufreq_ondemand
sudo modprobe cpufreq_powersave
sudo modprobe cpufreq_stats
sudo modprobe cpufreq_userspace
```

4.)Check to see if it worked:```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
cpufreq-info
```

5.)Set the governor you would like(One of the governors listed in the output of the commands in the previous step):```
sudo cpufreq-set -g <your governor here>
```

That should get it working. ^.^

---

### Post by ron66 on 2007-12-22
Thank you for these directions. I also have a Dell Inspiron 8100. This solution worked, until I  rebooted. Fortunately I was able to find another thread that explained a very similar solution that works on reboot.

[http://ubuntuforums.org/showthread.php?t=248867&highlight=speedstep-smi+ondemand](http://ubuntuforums.org/showthread.php?t=248867&highlight=speedstep-smi+ondemand)


:guitar:

ron66

---

