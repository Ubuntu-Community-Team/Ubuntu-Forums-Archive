---
title: "New intel video driver ?"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by jthirt on 2006-10-19
I've been battling with intel video driver i810 for two weeks now with limited success on a Gateway 400VTX laptop that refuses to set the pannel resolution to 1024x768 no matter what I do in the xorg.conf

I managed to get 1024x768 on an external CRT, but there is no way I can apply it to the LFP. ](*,) 

It is so frustrating to have that limitation. 800x600 is not good enough and that's the only problem I have with this laptop. 

Searching for posts, resources I found stuff related to git for an experimental version that, if I understand correctly may be the answer to my problem.

[http://www.intellinuxgraphics.org/documentation.html]("http://www.intellinuxgraphics.org/documentation.html")

There is says :

> There is an experimental version of the direct mode setting driver available via git: You're free to give it a try; it's published on the mode setting branch in the xf86-video-intel git repository. The mode setting branch supports the i810 through i945 hardware.

Is there any chance this will be available in a not too distant future on ubuntu ?

Did anyone try it ?

I would love to experiment, but I don't know where to start. :-k

---

### Post by kuja on 2006-10-19
If it's still deemed experimental, it will probably be quite some time before it's available in the Ubuntu repositories. Probably not until there is a beta or something of that nature.

---

### Post by DarkN00b on 2006-10-19
i915resolution didn't work for you? It usually can fix this problem.

---

### Post by almahtar on 2006-10-20
Yeah, have you tried 915resolution?  It helped me to get widescreen working on my mac mini.  Adding the line "915resolution 5c 1680 1050" in the startup section of /etc/init.d/gdm fixed all that.

---

### Post by jthirt on 2006-10-20
915resolution is not the answer. The problem apparently is that the driver only uses Built-in modes and only 640x480 and 800x600 are available as such. 

What I do not understand is why it can output to an external monitor in 1024x768 and not on the local panel. That's why I've experimented many different configurations but none did the job. 

All this with what I understood to be the latest driver from 

[http://www.fairlite.demon.co.uk/intel.html]("http://www.fairlite.demon.co.uk/intel.html")

So I've been searching for alternatives and found that intellinuxgraphics site. 

I keep hoping it takes me further ...

---

### Post by almahtar on 2006-10-25
> **jthirt said:**
> 915resolution is not the answer. The problem apparently is that the driver only uses Built-in modes and only 640x480 and 800x600 are available as such. 

Right.  This is precisely the problem that 915Resolution solves.  Did you try running the commands I suggested?  All of them? In that order?

*edit* The above is invalid.  I thought this was a different post.  My mistake.  The issue here is likely related to your refresh rate.  Good news is that there is still hope for you.  I'll explain in the edit below...


> **jthirt said:**
> What I do not understand is why it can output to an external monitor in 1024x768 and not on the local panel. 

1024x758, not being a widescreen resolution, is one of the Built-in modes of the Intel drivers.  That's why.  915Resolution adds wide-screen modes:  standard ratio modes are already working in the Intel drivers.

*edit* Again, the above is invalid.  I'm sorry about that. I thought I was responding to a different post.  The thing is, it's more complicated than simple XxY resolution: refresh rate and modelines have to be taken into account.  915Resolution can do this, as well, but it takes some research.  Chances are your LCD and your CRT are working at different refresh rates.  Getting an LCD to properly report its refresh rate and getting the Intel drivers to perform at that rate seems to be somewhat buggy.  It's going to require that you set your modeline correctly both with 915Resolution and in your xorg.conf.  Finding out the specific modeline settings for your display will, as far as I can tell, require googling.  Sorry :-(

> **jthirt said:**
> All this with what I understood to be the latest driver from 

[http://www.fairlite.demon.co.uk/intel.html]("http://www.fairlite.demon.co.uk/intel.html")


I've been hoping to find drivers better than the i810 in the Dapper (and Edgy... tried both) repositories.  I have not: it's the best as far as performance, stability, and compatibility that I've found.

---

### Post by jthirt on 2006-10-26
Hi almahtar,

I guess I should have been clearer on the fact that I think I already exhausted the possibilities offered within the limits of the 'current' i810 driver and related hacks. :-k 

So I am now investigating the **new** and **experimental** mode setting driver as it sounds like this should be the solution. At least to my local display panel problem. 

If you're interested, check out [this]("http://www.ubuntuforums.org/showthread.php?t=281275&highlight=modesetting") thread.

I'm stuck at the moment as I can't use git due to some silly firewall rules and I gave up fighting the guys in charge. ](*,)  If only I could get my hands on the notes I took to bypass the firewalled gateway ...  :twisted: 

Cheers,
jt

---

### Post by jwl007 on 2006-10-28
Any luck yet?

---

### Post by almahtar on 2006-11-01
> **jthirt said:**
> Hi almahtar,

I guess I should have been clearer on the fact that I think I already exhausted the possibilities offered within the limits of the 'current' i810 driver and related hacks. :-k 

So I am now investigating the **new** and **experimental** mode setting driver as it sounds like this should be the solution. At least to my local display panel problem. 

If you're interested, check out [this]("http://www.ubuntuforums.org/showthread.php?t=281275&highlight=modesetting") thread.

I'm stuck at the moment as I can't use git due to some silly firewall rules and I gave up fighting the guys in charge. ](*,)  If only I could get my hands on the notes I took to bypass the firewalled gateway ...  :twisted: 

Cheers,
jt

As far as the 915res stuff, the problem is that I don't know your experience level so when you say you've "tried it" I don't know what you actually tried.  Some people see the command "915resolution -l" somewhere, try it, see their problem isn't fixed, and move on: not realizing that the -l command does nothing for you. :-)  Sorry if it felt like I was ignoring what you were saying or insulting your intelligence.  I was just trying to make sure I knew exactly what you'd tried.

Have you had any luck with git?

---

### Post by jthirt on 2006-11-02
No worries mate! I've been there, being involved with support for many years ... It's always good to check the basics and often in these forums it is assumed people know things they don't always know. 

I have managed to compile and install the git mode setting driver, but it failed miserably ... So I reverted back to the previous one that worked. 

I'll try again when I find time for this, but the later I do the best my chances are of seing some progress on that front I suppose. 

I have a few more weeks ahead of me before Christmas, when I should return the laptop to it's actual owner ...

---

### Post by cmichaelboyd on 2006-11-02
You didn't post your xorg.conf, so let me run through a few things to make sure your tried them all.
 
did you:
 
1)  In the monitor section, add a line that says 
 
"VertRefresh 30-50" 
 
and another line that says 
 
"HorizSync 59-75" (these are generic values...but they should work just fine for your display).
 
2) In the device section, add a line that says 
 
"VideoRam *[insert amount of ram here]*" (this is in kilobytes, so 8 MB would be 8192).
 
3) If all else fails, insert a line in the "screen" section that says
"Modeline "1024x768@60" 64.56 1024 1056 1296 1328 768 783 791 807

"
 
 
These may seem like simple things, but you didn't mention them, so I thought I'd ask.  Also, if that modeline i listed above doesn't work for you, visit [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) to calculate another one.
 
Let me know if I've stated the obvious, or if I helped.
 
Thanks
Chris

---

### Post by jthirt on 2006-11-07
I have tried many things and searched for anwers in many places to finally get to the conclusion that the solution may come as part of the intel modesetting driver as indicated [here]("http://www.ubuntuforums.org/showpost.php?p=1725609&postcount=30")

I just raised a [bug]("https://bugs.freedesktop.org/show_bug.cgi?id=8929") on freedesktop.org to expose what I found out so far. ](*,) 

Let's hope this takes us (a few others share the same issue) forward. 

Thanks for your assistance anyway. 

BTW, you switched HorizSync and VertRefresh values I'm affraid ... ;) The way they are above crashes X ...

---

### Post by cmichaelboyd on 2006-11-09
sorry about that!  :mrgreen:

---

