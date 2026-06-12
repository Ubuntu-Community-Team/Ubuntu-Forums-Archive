---
title: "ATI Driver (Slow Restoring Windows)+ Jaunty + Mobility Radeon 3400 Series (Vaio FW)"
date: 2009-04-27
forum: Hardware
---

### Post by INTERPEGASUS on 2009-04-27
I am using the Ubuntu Jaunty 9.04 and I have noticed that enabling the ATI driver degrades performance on the following cases:

1-> When restoring a minimized window.
2-> When switching video to full screen.

Without the ATI driver restoring a window takes less than a second. Switching to full screen video is also very fast.

But with the ATI hardware driver it can take 2-3 seconds to restore a minimised window and 4-5 seconds to switch to full screen video using VLC.

Does anybody how to fix this issue?
thanks in advance!

---

### Post by INTERPEGASUS on 2009-04-27
Does anybody know how to troubleshoot this? 
Is compiz what is causing the problem?

---

### Post by EuGis42 on 2009-04-28
Try some of these:

[http://ubuntuforums.org/showthread.php?t=1136172](http://ubuntuforums.org/showthread.php?t=1136172)

---

### Post by s3lekta on 2009-04-28
> **INTERPEGASUS said:**
> I am using the Ubuntu Jaunty 9.04 and I have noticed that enabling the ATI driver degrades performance on the following cases:

1-> When restoring a minimized window.
2-> When switching video to full screen.

Without the ATI driver restoring a window takes less than a second. Switching to full screen video is also very fast.

But with the ATI hardware driver it can take 2-3 seconds to restore a minimised window and 4-5 seconds to switch to full screen video using VLC.

Does anybody how to fix this issue?
thanks in advance!


i to have a vaio-fw seriers with a 3400hd which currently has 8.10 installed through wubi ... i updated through the update manager to 9.04, then got black screen, fixed that when logged into prompt and ran the ati drivers off the site

after all of that things are all choppy and cpu / ram going nuts

how did you install 9.04.... fresh or upgrade?

---

### Post by s3lekta on 2009-04-28
any others who have a vaio-fw series successfully running 9.04?

---

### Post by s3lekta on 2009-05-01
> **INTERPEGASUS said:**
> I am using the Ubuntu Jaunty 9.04 and I have noticed that enabling the ATI driver degrades performance on the following cases:

1-> When restoring a minimized window.
2-> When switching video to full screen.

Without the ATI driver restoring a window takes less than a second. Switching to full screen video is also very fast.

But with the ATI hardware driver it can take 2-3 seconds to restore a minimised window and 4-5 seconds to switch to full screen video using VLC.

Does anybody how to fix this issue?
thanks in advance!

did anyone manage to figure this out?

Thanks

---

### Post by mysimbaa on 2009-05-06
> **s3lekta said:**
> i to have a vaio-fw seriers with a 3400hd which currently has 8.10 installed through wubi ... i updated through the update manager to 9.04, then got black screen, fixed that when logged into prompt and ran the ati drivers off the site

after all of that things are all choppy and cpu / ram going nuts

how did you install 9.04.... fresh or upgrade?


Hi,

I already gave a problem with my ATI graphic card 3400 HD.
Everytime I tried to activate the 3D acceleration it ends with a blanck screen at the boot of the ubuntu (Jaunty 9,04). So eachtime I have to reinstall all!! (form yesterday already 8 times installation -> quite painfull)

Could you please explain me how you fix the problem in the recovery mode?

Thanks in advance.

---

### Post by s3lekta on 2009-05-07
> **mysimbaa said:**
> Hi,

I already gave a problem with my ATI graphic card 3400 HD.
Everytime I tried to activate the 3D acceleration it ends with a blanck screen at the boot of the ubuntu (Jaunty 9,04). So eachtime I have to reinstall all!! (form yesterday already 8 times installation -> quite painfull)

Could you please explain me how you fix the problem in the recovery mode?

Thanks in advance.


follow some of the steps found in this thread --> [http://ubuntuforums.org/showthread.php?t=1133931&highlight=ati+3400+hd](http://ubuntuforums.org/showthread.php?t=1133931&highlight=ati+3400+hd)

---

### Post by mysimbaa on 2009-05-08
> **s3lekta said:**
> follow some of the steps found in this thread --> [http://ubuntuforums.org/showthread.php?t=1133931&highlight=ati+3400+hd](http://ubuntuforums.org/showthread.php?t=1133931&highlight=ati+3400+hd)


Thank you for your reply.
Did you manage to get your ATI 3400 working with the fglrx?

Please if someone find out how to get it working fine let us know. For my side too.

See ya

---

### Post by s3lekta on 2009-05-12
> **mysimbaa said:**
> Thank you for your reply.
Did you manage to get your ATI 3400 working with the fglrx?

Please if someone find out how to get it working fine let us know. For my side too.

See ya

i got it to work, but again it is slow minimizing / maximizing and things are a bit choppy

did upgrade / fresh install and same deal

we will just have to wait for a solution

---

### Post by uptheirons1 on 2009-05-15
I have the same problem. Windows minimized and maximized very slowly. I replaced my window manager with xfwm4 ("xfwm4 --replace" in the terminal and you can add that command to the startup programs to make it the default window manager) and it went a little faster, but it was still choppy. I think I am just going to go back to Intrepid and wait for Karmic Koala.

---

### Post by grigio on 2009-05-18
I have the same problem

---

### Post by fbkarsdorp on 2009-05-24
I'm on a Vaio-fw(3) series, running ubuntu jaunty 64bit using the fglrx driver (catalyst 9.4). I also noticed the restoring/resizing windows issue. Tried catalyst 9.5 which didn't fix it (in fact I lost video support...:?:). Today through trial and error I managed to get some improvement. From a 3 to 5 second delay to only say 1. Ok, not perfect but a lot better!!

This seems to be the problem. It is glxgears having very low fps with fglrx and that's because of PowerPlay. In the catalyst control center you can turn this off. 

Hope it helps.

---

### Post by kopus on 2009-06-16
There is also another issue, besides this one I also can't get the multiple display to work. It sticks to "clone mode".
On Intrepid everything worked fine.

---

### Post by FischBaum on 2009-06-20
had the same prob. 

i turned off the visual effects (System>Preferences>appearance>visual effects)

now, the problem is gone (but also the eye-candy)

---

### Post by depaulmatthew on 2009-06-23
I followed the instructions on manually installing the driver. It worked fine for me. 

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)


> **FischBaum said:**
> had the same prob. 

i turned off the visual effects (System>Preferences>appearance>visual effects)

now, the problem is gone (but also the eye-candy)

---

