---
title: "NVIDIA 169.09 Linux Display Driver is out"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by NilsHG on 2008-01-22
[http://www.phoronix.com/vr.php?view=11711]("http://www.phoronix.com/vr.php?view=11711")

Here is the story.

Anyone tried it yet? I am reluctant trying it out for now. my system works fine with the current driver and the fan problem is worked around with nvclock. i broke my running systems far to often recently to be the first to jump for the new nvidia driver ;)

report your experience with the new thing. :popcorn:

---

### Post by KThrace on 2008-01-24
I just tried it. I've been using the one in the repos since Gutsy was released, and between the two I'm gonna stick with the new 169.09 version. It seems to have solved the problem with having Compiz Fusion running and switching between virtual terminals and X, plus now my machine comes out of hibernation properly. Video rendering appears *slightly* faster, though it may just be a placebo.

Anyways, since there are no obvious problems with it I'm gonna keep using it.

---

### Post by scizzo on 2008-01-24
nice to see that they have fixed the 100% fan speed problems. since before you had to use the nvclock to reduce that to auto or simular.

---

### Post by henriquemaia on 2008-01-24
> **KThrace said:**
> I just tried it. I've been using the one in the repos since Gutsy was released, and between the two I'm gonna stick with the new 169.09 version. It seems to have solved the problem with having Compiz Fusion running and switching between virtual terminals and X, plus now my machine comes out of hibernation properly. Video rendering appears *slightly* faster, though it may just be a placebo.

Anyways, since there are no obvious problems with it I'm gonna keep using it.

How did you installed it? I have tried the Nvidia installer, but when starting X I get an error message: 

"screen(S) found, but none have a usable configuration".

---

### Post by jimbojones on 2008-01-24
What do you have to uninstall from a default Ubuntu Gutsy install to be able to manually install 169.09.  I get conflicts with already installed kernel modules  Thanks

---

### Post by henriquemaia on 2008-01-24
I installed through envy. Now I&#8217;m running 169.09.

I don&#8217;t have any issues yet, but I haven&#8217;t tested it thoroughly.

---

### Post by jimbojones on 2008-01-24
Downloaded Envy & it worked without any intervention.  I usually try to do things by hand so I can backtrack if I hit trouble, so Ill take a peek at the script and see what it had uninstalled first.  Thanks

edit.  Desktop effects don't seem to work, tells me I need to enable the Nvidia restricted driver...I am a little bit leary about enabling that and having it download the old driver again.

---

### Post by ph1 on 2008-01-24
jimbojones, does that mean that Compiz-Fusion doesn't run at all with the new driver?

Does anyone who is experiencing the black screen flash due to the shifting in clock settings know if this driver fixes this problem at all?

---

### Post by Lvcoyote on 2008-01-25
Installed 169.09 tonight using Envy.  Envy has been updated as of today to install the 169.09 drivers.  Everything works fine for me including Compiz-Fusion.  My fan speed has returned to normal and the graphic interface seems much smoother, I like this driver quite well.

Remember to uninstall the previous drivers using the command listed on the main envy page, its in a red warning box, should be easy to see how to uninstall....LOL

---

### Post by TheValk on 2008-01-25
> **Lvcoyote said:**
> 
Remember to uninstall the previous drivers using the command listed on the main envy page, its in a red warning box, should be easy to see how to uninstall....LOL

I looked on the Envy site Ubuntu FAQ
> 

G) Shall I uninstall the ATI/NVIDIA driver before I install a new version of the driver through Envy?

Envy will do it for you. However if you want to uninstall the driver, nothing bad will happen ;) 



Which is what I did to go from 169.07 to 169.09.

Nothing bad happened, thank the computer gods.   :)

---

### Post by ElTimo on 2008-01-25
Installed, got the same problem as henriquemaia. running a Quadro 110m (GeForce 7300m with different firmware).

---

### Post by jimbojones on 2008-01-25
> **ph1 said:**
> jimbojones, does that mean that Compiz-Fusion doesn't run at all with the new driver?


Well, it seems other people have no issues....since I updated I can not use the default visual effects setting.  I removed the restricted driver, installed with Envy, then I was told I need to enable the restricted driver before I can use Desktop Effects.  Once I do that and apply the effects, I lose all my window borders and my terminal screens are blank white :confused:  Im not really concerned, but it does seem odd.

---

### Post by johnnyzazza on 2008-01-25
> **ph1 said:**
> jimbojones, does that mean that Compiz-Fusion doesn't run at all with the new driver?

Does anyone who is experiencing the black screen flash due to the shifting in clock settings know if this driver fixes this problem at all?
This may help:

How to stop screen from flickering (NVIDIA 7900GS)

Add the following to /etc/modprobe.d/options:

> options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"

---

### Post by lemurian on 2008-01-25
I've gained 169.09 as a side effect of upgrading to Hardy's kernel 2.6.24-5.  No issues here.

One thing I've noticed is that now if I hit the key combination to switch between the internal LCD and an external monitor (Fn-F3 on my laptop), in addition to the two modes previously supported (LCD only or monitor only) now there is a third mode in which both the LCD and monitor are displaying.

---

### Post by Nando777 on 2008-01-31
It doesn't work for me, what a surprise. Every time I need to fix something in Ubuntu (quite often) I waste an entire day and I only get half solutions. 

I uninstall restricted driver, I install new driver and every time I try to see the desktop effects it says I need to use the restricted driver. Yet if I run nvidia-settings from the console the thing is there, I can do the changes but the driver isn't working... can anyone PLEASE explain how to do this in the precious Ubuntu and actually make it work?

By the way, I love it how updates in Ubuntu are so prompt to show up for everything (like open arena) except for things that really matter -- like drivers. 

I don't mean to be rude, the operating system is nice and free but these issues are so annoying. 

Thank you.

---

### Post by dabl on 2008-01-31
1. Download Envy from here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

( you want the file 0.9.10-0ubuntu2 - click "Get Envy New")


2. Right-click the downloaded file and "open with Gdebi" or whatever it says to install it.

3. If it happens to error out on a dependency problem, just note down what file it lacks, and use the console window to apt-get it.  Then try again with Gdebi to install Envy.

4. When Envy is installed, you can run it either of two ways:

    (a) open the console and enter "sudo envy -t"  (this is particularly useful after a kernel upgrade!)
    (b) Click on the purple Envy icon in your System folder

Follow the instructions to install the latest Nvidia driver.  :guitar:

---

### Post by Nando777 on 2008-01-31
Thank Dabl

I already fixed it. That envy software did the trick and then when it asked me to enable the restricted driver I clicked okay and it was fine.

You see I couldn't do it before because it reinstalled everything from the package manager and it destroy the update but with Envy it was okay. 

Now I have the Compiz effects to the maximum. I am looking to see if it'll give me the same errors it gave me before. I had a lot of problems with the previous version -- the one that comes with Ubuntu

Thanks again for your help.

---

### Post by dabl on 2008-01-31
:cool:

Thanks to Alberto Milone, actually.  :)

---

### Post by deepclutch on 2008-02-02
No repos for new driver?many n00b's  with 8800GTS etc cards are suffering :( some backports for gutsy?pls share here if you know!
[http://www.thinkdigit.com/forum/showthread.php?t=79545](http://www.thinkdigit.com/forum/showthread.php?t=79545)

---

