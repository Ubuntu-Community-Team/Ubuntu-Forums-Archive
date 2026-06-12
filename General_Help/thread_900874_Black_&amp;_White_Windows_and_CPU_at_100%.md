---
title: "Black &amp; White Windows and CPU at 100%"
date: 2008-08-25
forum: General Help
---

### Post by bilijoe on 2008-08-25
I have been using Ubuntu 8.04.1 for about a month (since it came out), with almost zero problems. I have a DELL Optiplex GX270 with a 2.88GHz Hyperthreading Pentium, Hyperthreading enabled, and 4Gb of RAM. It seems as if this system should flat scream, but it seems to have been getting slightly slower with time. 
 
I used to rarely have a window turn Black and White, and become unresponsive for a while. At first, I assumed the process was hung, and killed it, but I've found out that if I am patient, these windows always come back to life. Recently, the B&W window thing has been happening freequently enough to be annoying. It seems to happen under only a few circumstances. One scenario is when I open a folder containing lots of short video clips (75 or more), "select all", and then open any one with Totem Movie Player, VLC Player, or Mplayer (doesn't seem to make any difference which I use). 
 
While the clips are loading (I assume that's what is happening), both the folder window containing the clips, and the player window will turn B&W, and it can take up to 30 or 45 seconds before, first the folder window, and then the player window return to color, and the clips start running.
 
Also, sometimes when I open an Internet site, especially if I already have 4 or 5 tabs open, the Browser window (FireFox, of course) will go B&W and stall, but most often when I CLOSE a tab. Also, if I download a file, or read an email with an attachment (that gets downloaded in order to view it), either when the download completes, or when I close the Browser, I get the B&W thing. 
 
 
While this is happening, the CPU shows in the System Monitor as having one or both of the processors at or very nearly at 100% (Hyperthreaded processor shows as having 2 CPUs). Under a "normal" heavy load, it's unusual for either processor to go over 25%. If I look at the running processes while a window is B&W, nautilus always shows heavy processor usage--between 50% and 100%. Also, Xorg, Gnome Panel, and Gnome System Monitor, and sometimes FireFox will show between 25% and 50% processor usage (once in a while higher--up to 85% or 90%). Nautilus and Totem (or whichever player I'm using) usually take the highest percentage of the CPU, with Nautilus being on top more of the time; sometimes FireFox will grab 80% or 90% and take the top spot. The Gnome System Monitor is usually at the botom, sometimes with only a percent or two, but will often jump up to 25% to 50% for a while. 
 
When viewing the Resources graph, both CPUs stay slammed up against the 100% mark. During this time, the System Load shows averages between 1.5% and 3%. Once the windows return to color mode, and the clips start playing, Xorg will sometimes hit 50% when switching from one clip to the next, sometimes even 100%, but most of the time, the only process that shows "running" is the Gnome System Monitor which stays at 0 or 1%. If you watch the Resources graph, it shows both the processors periodically hitting at or near the 100% mark, but not at the same time, and it's a short-lived peak. They seem to average (according to the graph) between 10% and 25%. usually between 15% and 20%. Load averages run between 0.5% and 1.0%.
 
With VLC, during the B&W period, only CPU2 runs a [near] constant 100%, CPU1 varies between 35% and 85% or so, and the time before color, and normal operation returns is about half what it is with Totem. Once the clips start running, VLC appears to use far less resources, though Xorg will sometimes still hit 85% when switching clips.
 
It's harder to duplicate the download thing, so I don't have specifics for that, but the behavior is very similar, so I assume pretty much the same things are happening.
 
As I said, this used to be a rare occurrence, now, it happens [almost] every time I load up a bunch of clips, and fairly freequently after a download. Also, I have to wonder what the blazes the machine is doing, during the B&W period. With a 2.88GHz P4, supported by 4Gb of ram, it seems like at 100% CPU usage, almost any task should complete in the blink of an eye. It also seems like, at 100%+100%, the thing should be smoking--literally--smoke coming out of the box.
 
I have played around with this for over a week now, and I'm at a complete loss for any explanation of what's going on here. Since it seems to slowly be getting worse, I would really like to get this figured out, and fixed (I say "fixed", because I assume something is not working correctly--this can't be "normal" for a machine like this--and it didn't used to happen at all, then infreequently, now, several times a day).
 
Let's se, what else might be useful that I haven't mentioned. The HDD is a 250Gb Maxtor SATA drive. Two of the four Gb of RAM are Kingston, the other two are PNY, both matched 1 GB sticks, in appropriately paired sockets. This is a "pure" Ubuntu-Linux system--no dual booting here. I've got a lot of little whiz-bangs and gizmos loaded, mostly FireFox extensions and plug-ins. The two optical drives are both new, both LiteOn, one with LightScribe. And, as I said, except for this B&W thing, I have had ZERO problems with this installation.
 
So, if anybody can offer any helpful advice, or a "how to", article, or previous post that might shed some light on what's going on, I'd really appreciate it. (I looked for previous posts, but I don't seem to have any luck with the search these days, since the forum change a couple of months back.) Anyway, I hope somebody can help me with this; I'm frustrated! :confused:

---

### Post by bilijoe on 2008-09-01
The problem is definitely getting worse.  Now, almost any window is likely to go B&W, if only for a second or two, but sometimes windows stay B&W for quite a long time (5, maybe 10 minutes).  It seems most often, FireFox, or a media player is using the window, but like I said, now it seems any window is susceptible to this strange phenomenon.  

I understand that it is because either the program has hung, or the system THINKS it has hung.  My experience is, the program becomes unresponsive, and the window turns B&W.  I have a DELL Optiplex with a 2.88 GHz Multithreading Pentium 4, and 4 GB of RAM.  I can't understand why the kind of programs usually running when this happens would become unresponsive, especially with the resources my computer has available.  

I have not been able to determine any pattern to this, just that it is happening more and more often, and on more kinds of windows (now including File Browser windows).  This (the unresponsive part--I can put up with B&W, on and off) is getting irritating.  For all the weird and disgusting things my various different Windows installations did, none of them ever did anything like this.  (Of course programs would become unresponsive, which, under Windows usually required a reboot, so this is still better, but it's getting really tiring.  I'm not used to having to wait for a computer any more.  

20, 25 years ago, it was common to have to wait for this or that, often just for a HDD write to complete, but for the past ten years at least, I haven't had to wait for a computer to do anything--except waiting, seemingly endlessly, for Windows to boot up or shut down.  What in blazes is Windows DOING all that time while it is shutting down?  And what "settings" can it possibly be saving that take so long to (I assume) write to the disk?

Anyway, can someone PLEASE give me some feedback on this?  If it's a kernel issue (I don't think it is, but I don't know), where do I go for help with that?  ANY feedback would be appreciated.  This thread has just been lying there like a dead fish.  Is it so bad that nobody wants to touch it?  H E L P !!!

---

### Post by 3rdalbum on 2008-09-01
It's difficult to diagnose.

Maybe try running the command:

top

in a terminal, and take a look at what the top program is when the windows turn grey. This could help us. I'm not sure if the Pentium 4s are 64-bit, so you're really only running with somewhere around 3 GB of RAM anyway.

After a window goes grey, you could run the "dmesg" command and have a look at the bottom of the listing, see if there's an error message from the kernel.

---

### Post by bilijoe on 2008-09-01
The Pentium 4 is only a 32-bit processor.  All the System reporting tools show 3.5Gb RAM available,  The P4 I have in this system is the Hyperthreading version, which *usually* shows 2 CPUs (just like the Core Duos) in the System Monitor's Resource graph.

I have run TOP.  I don't remember exactly what it showed, but I remember it was very similar to the list of processes shown in the System Monitor.  In that list, Xorg, Gnome Panel, and Gnome System Monitor, and sometimes FireFox will show between 25% and 50% processor usage (once in a while higher--up to 85% or 90%). Nautilus and Totem (or whichever player I'm using) usually take the highest percentage of the CPU, with Nautilus being on top more of the time; sometimes FireFox will grab 80% or 90% and take the top spot. The Gnome System Monitor is usually at the botom, sometimes with only a percent or two, but will often jump up to 25% to 50% for a while.

When viewing the Resources graph (using Totem), both CPUs stay slammed up against the 100% mark. During this time, the System Load shows averages between 1.5% and 3%. Once the windows return to color mode, and the clips start playing, Xorg will sometimes hit 50% when switching from one clip to the next, sometimes even 100%, but most of the time, the only process that shows as "running" is the Gnome System Monitor which stays at 0 or 1%. If you watch the Resources graph, it shows both the processors periodically hitting at or near the 100% mark, but not at the same time, and it's a short-lived peak. They seem to average (according to the graph) between 10% and 25%. usually between 15% and 20%. Load averages run between 0.5% and 1.0%.
 
With VLC, during the B&W period, only CPU2 runs a [near] constant 100%, CPU1 varies between 35% and 85% or so, and the time before color, and normal operation returns is about half what it is with Totem. Once the clips start running, VLC appears to use far less resources, though Xorg will sometimes still hit 85% when switching clips.
 
I'll try the dmesg thing later today, and see what it says.

To me, the most curious aspect of this is that it is definitely getting worse over time.  It used to happen, maybe once or twice a Month--now it happens every time I use the computer.  And, it's happening with window types that it did not used to happen with--File Browser windows, for example.  I'm really not used to problems with Linux (period) that get progressively worse.  It's reminiscent (dare I say it) of Windows getting progressively slower and slower due to uncontrolled growth of the registry--but that can't be a factor here.  What on Earth could be changing, in the system, that would cause a problem like this to get worse with time.  I'm befuddled! :confused:

The other thing I noticed is that the length of time a window is B&W, is getting longer and longer.  It used to be only 5 seconds, or less.  Now, it can be a minute or more.

I've run the Memory test from the Ubuntu Install disk, to rule out a failing memory chip, but found no problems.

I'll post the results of dmesg, and also the list from TOP, later today.

Thanks.

---

### Post by bilijoe on 2008-09-03
OK, the top four applications according to both top and the System Monitor are: Nautilus, FireFox (running Pandora Radio), totem, and gnome panel.  They exchange positions often, but are consistently the top four, and all show between 25% and 85% processor use (it varies for each one, over time).  Everything else in the list shows 0% processor use--most show "sleeping".  The Resources graph in the System Monitor shows both CPU1 and CPU2 at a constant 99% to 100%, most of which is shown as "user", a small amount as "system".  

I don't really know what I'm looking at in the output from dmsg, but none of it looked like any kind of error message.  The problem still seems to be getting worse.  I have some folders that contain 300 or 400 files--pictures and video clips mostly.  I keep meaning to organize and separate them, but haven't yet. Could this be a problem? 

There is a program I play around with once in a while at [COLOR=Red]_[http://www.jacksonpollock.org/](http://www.jacksonpollock.org/)_[/COLOR].  The other day, I was fiddling with that, and got a B&W window.  Nothing else was running except FireFox running that site.  It really doesn't seem like I'm running this system that hard, most of the time, and, from what I understand, the B&W windows result from Gnome(?) seeing that the window has become unresponsive, but, sometimes the window is NOT unresponsive when it goes B&W. 

I have now seen this on one of my other computers--also running Ubuntu-Linux 8.04.1.  This one has a normal (i.e., not multithreading) 2.66 MHz Pentium 4 with only 512 Mb of memory.  I've only seen the B&W window once on it, so far.  At this point, that's all I know.  Are there any other tests I can run, or any other things to look at?

---

