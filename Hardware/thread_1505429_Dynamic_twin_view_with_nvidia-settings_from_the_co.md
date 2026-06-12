---
title: "Dynamic twin view with nvidia-settings from the command line?"
date: 2010-06-09
forum: Hardware
---

### Post by bademeister on 2010-06-09
Dear all,

I have an nvidia card (9400, i believe) in my 13.3" macbook pro and am frequently changing my monitor setup, i.e. at my office and at home i have an additional 22" monitor hooked up to the dvi port (actually apples weird port with a dvi connector) while on the road I have not.

I don't have the twin view configuration set  in the xorg.conf config file as this behaves funny if you don't have a second monitor connected (your mouse cursor and windows might be beyond what you can see on the small monitor). So what I do each time that I connect an external monitor is to run the GUI of the nvidia-settings tool and enable twin view for the external monitor and position it where I want it. Annnooooyyyying!!! especially if you do it several times a day.

So I wanted to write a script that I can just run (maybe automatically even if a second monitor is detected, this shouldn't be too hard) to  set up everything how I want it. Small problem: I cannot, for the life of me, figure out how this nvidia-settings command line tool works. I have tried a few things such as

```
nvidia-settings --assign AssociatedDisplays=0x00030000 
```

(this is the value being displayed when I have both monitors enabled and run 
```
nvidia-settings --query all
```
)

Most other attributes seem to be "read-only" (such as the seemlingly promising "TwinView" or "EnabledDisplays". I've looked into the man pages and searched the web high and low, but to no avail. 

Any help on this would be really truly very highly appreciated ;)

Thank you
Paul

Oh, yes, this is on ubuntu lucid 10.04 amd64 with the current 195 nvidia driver.

---

### Post by bademeister on 2010-06-13
gentle bump ;)

---

### Post by t.rei on 2010-06-23
This would actually be of great interest to me, as I also use a second monitor @ home, but ofcourse I don't take it along on the train. ;)

Unfortunately twinview stopped working smoothly some month or two ago, but I haven't noticed, because my computer was home.

Now everytime I want to connect my second monitor, I need to edid xorg.conf and comment/uncomment the twinview lines. Switching while having the xserver running ends up giving me garbage on both screens until switching back because I don't confirm.

Having it set in xorg.conf works fine. 

But this is even MORE anoying then the nvidia-settings-clickage. :D

any advice?

---

### Post by t.rei on 2010-06-23
A little note:

This happens with all versions of the nvidia drivers I have tried, even the previously working ones:
NVIDIA-Linux-x86-190.42-pkg1
NVIDIA-Linux-x86-190.53-pkg1
NVIDIA-Linux-x86-195.36.31-pkg1
NVIDIA-Linux-x86-256.35

*sadpanda*

---

### Post by jugglefish on 2010-08-30
> **bademeister said:**
> 
...
So I wanted to write a script that I can just run (maybe automatically even if a second monitor is detected, this shouldn't be too hard) to  set up everything how I want it. Small problem: I cannot, for the life of me, figure out how this nvidia-settings command line tool works. I have tried a few things such as ...


Did anyone get any further on this matter yet?

---

### Post by dargaud on 2010-08-30
Wouldn't it be possible to have a small script:
- turn off X server
- switch between two xorg.conf files
- turn X back on
???

---

### Post by t.rei on 2010-08-30
That is basically exactly what I have done. It works, but ofcourse defeats the concept of "oh I need more screen realestate - turn on second monitor / oh I want to watch a movie on the couch - turn off second monitor" way of 'working'. 

So far, the nvidia-settings still garble my screens.

The driver I am using right now is:
NVIDIA-Linux-x86-256.44.run (from nvidia-website)

---

### Post by jugglefish on 2010-08-30
> **dargaud said:**
> Wouldn't it be possible to have a small script:
- turn off X server
- switch between two xorg.conf files
- turn X back on
???

this of course is possible but a) takes time and b) destroys the current state of the applications.

nvidia-settings does the job for me quite nice, except for the need of a bunch of clicks.

There seems to be some help in form of a C API and some example "clients" for the "NV-CONTROL extension", additional to the nvidia-settings GUI.

'nv-control-dpy' being one of them is even available as binary currently at least on debian testing/unstable. Seems like it only needs a little bit more knowledge to get this working towards a "just update my screen (remove/add/optimize TwinView) for current monitor setup" script.

Some experiments with 'nv-control-dpy --dynamic-twinview' and 'xrandr NEEDSINVESTIGATION' seem quite promising.

---

### Post by realzippy on 2010-08-30
the tool [disper]("http://willem.engen.nl/projects/disper/") might exactly do what you want...

---

### Post by jugglefish on 2010-08-30
Hello,

> **realzippy said:**
> the tool [disper]("http://willem.engen.nl/projects/disper/") might exactly do what you want...

fantastic! Thx a million, works out of the box and is exactly what I was looking for!

---

### Post by vdoki on 2010-09-24
> **realzippy said:**
> the tool [disper]("http://willem.engen.nl/projects/disper/") might exactly do what you want...

Thank You! I had the same problem for years. I used nvidia-settings at least once every day, to switch to the external monitor at work.

Disper does it with one command.

There is a ppa repositor, I recommend to install it from there:
[https://launchpad.net/~disper-dev/+archive/ppa](https://launchpad.net/~disper-dev/+archive/ppa)

Now it is this easy to switch to the external monitor and back:
disper -S -r auto
disper -s -r auto

---

### Post by perky on 2010-10-04
> **vdoki said:**
> Thank You! I had the same problem for years. I used nvidia-settings at least once every day, to switch to the external monitor at work.

Disper does it with one command.

There is a ppa repositor, I recommend to install it from there:
[https://launchpad.net/~disper-dev/+archive/ppa](https://launchpad.net/~disper-dev/+archive/ppa)

Now it is this easy to switch to the external monitor and back:
disper -S -r auto
disper -s -r auto

That is awesome, thank-you!  (and good-bye, for now, nvidia dialog!)

The commands I use:
disper -s
disper -e -t left

Would be good if someone figured out how to automatically execute the commands when plugging in/out an external monitor :D

---

### Post by sgiessl on 2010-10-13
Thanks a lot guys, I was looking for a solution like disper as well. :)

> **perky said:**
> Would be good if someone figured out how to automatically execute the commands when plugging in/out an external monitor :D

At least, it should be possible to bind disper to some key combo. For thinkpad, there is an acpid button script using disper as backend: [http://www.linux-depot.com/?p=projects&s=nvidia](http://www.linux-depot.com/?p=projects&s=nvidia)
I'm using a lenovo T61 and now I can cycle through the display modes using Fn+F7 :)

---

### Post by t.rei on 2010-10-26
Too sad. Something must be really wrong with my system. Disper runs into the same "both screens just garbled junk" as the nvidia-settings tool. Too bad this worked such a loooong time ago and just stopped working flawlessly. :( *sadpanda* This is actually gonna be a little embarassing next week, when I am going to have to use my computer for presentations... "hold on, let me just shut everything down, do some voodoo in cmdline, and start everything back up..." -.- Especially sad since I KNOW it worked.

---

### Post by phantom_ on 2010-11-12
*disper* is really great, works perfect with my notebook LCD and external LCD connected over VGA interface.

both display resolutions are 1680x1050.

however, GNOME panels remain at notebook display while all desktop icons go to external display.

i hardly found the solution with the program *gconftool-2*. this program commands GNOME configuration so that one can change GNOME top & bottom panel placement.

my twinview script is;
```
#!/bin/sh
disper --displays=auto --extend --direction=left
echo "Moving panels to the external display"
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_screen0/monitor" --type integer "1" 
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/monitor" --type integer "1"
```

and my singleview script is;
```
#!/bin/sh
disper --single
echo "Moving panels to primary display"
gconftool-2 --set "/apps/panel/toplevels/bottom_panel_screen0/monitor" --type integer "0"
gconftool-2 --set "/apps/panel/toplevels/top_panel_screen0/monitor" --type integer "0"
```

---

### Post by atropa on 2011-04-08
Awesome! Disper for the win

I've really been searching for months to achieve exactly this. Works
like a charm.

The above command using gconftool was really helpful too.

---

### Post by bpeyser on 2011-08-18
Thanks for the tip on *disper*!

Here is what I did:

I set up my dual displays the way I like them when my laptop is docked using NVidia's config tool, then at the terminal:
```

$ disper -p > dual-display.conf

```And did the same thing for single display:
```

$ disper -p > single-display.conf

```Then I just made executable shell scripts like:
```

 cat dual-display.conf | disper -i
 
```I made menu items that call the shell script--now I have a menu item to enable dual displays exactly the way I like them, plus another one to return to single display. Works great!

I could certainly make a more involved shell script that would cycle through my choices using the Fn-F8 key, but this works fine and I'm too lazy to make that work right now.

---

### Post by mrinvader on 2013-02-20
This happened to me except it was that x was configured correctly at the login screen, but something in my userprofile set it to clone after login. and i was too lazy to dig in my profile settings to remove clone and set twinview. Thanks A Million Indeed! :p:p

> Originally Posted by realzippy  
the tool disper might exactly do what you want...

---

### Post by overdrank on 2013-02-20
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

