---
title: "Suspend--&gt;shutdown?"
date: 2005-12-10
forum: Hardware &amp; Laptops
---

### Post by quietglow on 2005-12-10
My HP dv4000 has a tendency to wake from suspend to ram and immediately shut down. This happens maybe every 5th or 6th time I suspend, though it has happened both sooner and later.

Has anyone else had this problem and fixed it?

---

### Post by spier on 2005-12-11
This may be just a foolish answer, but this happens on my sony only when I use the Power button to wake it up! It wakes, but then it follows the key pressed`s function and shutdown!

---

### Post by quietglow on 2005-12-11
Yeah, I was having that problem too :-)

But no, it does it oftentimes when I just open the lid. I think it actually may be influenced by what programs are running--I'm trying to test as I have time.

---

### Post by quietglow on 2006-01-01
Anyone? I love my DV4000, but it does seem to have the ability to sense when I need to make quick check of something and shut down just for fun. I do a whole lot of going from meeting to meeting so suspend is important to me. 

When I get the unplanned shutdown, it is actually worse than if I were just starting it up since I lose anything unsaved AND I have to wait for it to shut down and then start back up (and we know that currently takes a LONG time).

More info: I can tell it happening because when it comes out of suspend I get maybe 10 seconds of a fully functional desktop and then it switches over to a console log-in screen. I've tried switching over to another console when it happens (ctrl-alt-f7) and it more or less just looks like its gotten the signal to shut down.

---

### Post by tbw on 2006-01-01
[QUOTE=quietglow]Yeah, I was having that problem too :-)

But no, it does it oftentimes when I just open the lid. I think it actually may be influenced by what programs are running--I'm trying to test as I have time.[/QUOTE]

Having the same issue with lid opening on a DV1331-- Let me know if you make any headway.
Thanks,
Tim

---

### Post by quietglow on 2006-01-01
> Having the same issue with lid opening on a DV1331-- Let me know if you make any headway.

That's odd since my wife's DV1000 has never done it...I wonder if its something with the wireless (since that seems to be one of the chief differences between them)

---

### Post by tbw on 2006-01-02
[QUOTE=quietglow]That's odd since my wife's DV1000 has never done it...I wonder if its something with the wireless (since that seems to be one of the chief differences between them)[/QUOTE]

Hi,

From what I can see it has to do with the way I'm putting mine to sleep.

To go into suspend to RAM mode, I'm doing echo mem > /sys/power/state
Which drops me into suspend like it should... now when I hit the power button or open the lid (by pressing the lid button deal) to wake it up, it comes back alive and immeidately shuts down.

-- Partial fix --
The power button script is always getting called from what I can tell..when you open and close the lid, as well as if you are hitting the power button to bring the machine back on.

I made two little hacks to a couple of the default scripts and I've at least got suspend to ram working -- let me know if this works for you...

in /etc/acpi/lid.sh script segment:

if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"
            . /usr/share/acpi-support/screenblank
        fi
    done

I added :

touch /var/lock/acpisleep
echo mem > /sys/power/state
-----------------------------------------------------------------------------

This has the effect of touching the file that power button script is looking for and then dropping us into sleep in ram mode.

Then in /etc/acpi/powerbtn.sh I changed:
[ -f /var/lock/acpisleep ] && exit 0

to

if [ -f /var/lock/acpisleep ] then;
            rm -rf /var/lock/acpisleep
            exit 0
fi
_____________________________________________________________

I know jack about bash scripting but the original seemed to me like it was just checking for the existence of the acpisleep file and if it found it it stopped the script.

My changes simply tell it to remove the file if it exists and then exit. (This way the   power button will still shut the machine down like it used to.... adding the removal of the file to the lid.sh file wasn't working because apparently the lid.sh isn't called when the lid is opened event is triggered from sleep?!?!... 
Go figure?!


I'm wondering what effect, if any, this will have on hibernate functioning... which at this point I still haven't got to work.

Hope this helps.
Tim

---

### Post by quietglow on 2006-01-02
Man you rock for going into those bash scripts: I've been putting it off cause I too know zip about scripting.

I'm gonna test your tweaks shortly, but I'm checking something else first. Are you using gnome power manager by chance? I noticed that both the lid and the power button scripts completely abdicate if gnome power manager is running. So basically none of the scripts in /etc/acpi are really running anything. Just for the heck of it, I've removed the power manager and am cycling it through sleep states. I'm about on the 8th or 9th sleep and no shutting down yet, so perhaps this may be it.

By the way, my hibernation works perfectly with the exception of the machine coming out of sleep without the trackpad enabled every now and again. I just don't use it since it take 75% of the time a boot does anyway.

I'll post more when I know more.

---

### Post by tbw on 2006-01-02
[QUOTE=quietglow]Man you rock for going into those bash scripts: I've been putting it off cause I too know zip about scripting.

I'm gonna test your tweaks shortly, but I'm checking something else first. Are you using gnome power manager by chance? I noticed that both the lid and the power button scripts completely abdicate if gnome power manager is running. So basically none of the scripts in /etc/acpi are really running anything. Just for the heck of it, I've removed the power manager and am cycling it through sleep states. I'm about on the 8th or 9th sleep and no shutting down yet, so perhaps this may be it.

By the way, my hibernation works perfectly with the exception of the machine coming out of sleep without the trackpad enabled every now and again. I just don't use it since it take 75% of the time a boot does anyway.

I'll post more when I know more.[/QUOTE]


I saw the pidof PowerManager -- I wasn't running it. When I installed it I got the same issues though... pidof PowerManager won't return anything though, the process for the gnome power manager is gnome-power-manager -- which is the only thing I could get to return a pid to me once I had the power manager installed.

THe power manager locked up on my machine so I removed it. But it seems like you've got yours working great...

Congratz.

My hibernate sucks personally, it never works... i even made sure i added the resume partition to be my swap part and everything...i tell it to hibernate, it does it's thing ut when I bring it back up it just shows me half a page of logs and sit there forever.

---

### Post by quietglow on 2006-01-02
lol...I just got home, read your post and opened my laptop...and it shut down. Okay, on to trying out your changes. So you haven't gotten any unplanned shutdowns since you made the changes?

---

### Post by tbw on 2006-01-02
[QUOTE=quietglow]lol...I just got home, read your post and opened my laptop...and it shut down. Okay, on to trying out your changes. So you haven't gotten any unplanned shutdowns since you made the changes?[/QUOTE]
Nope and I let it sleep all night last night -- I find the problem and get it fixed until after midnight... I got up at 11 -- and it woke right up...

---

### Post by quietglow on 2006-01-02
I meant to ask this before...do you think it's time dependent? I notice it seems to happen more when its been sleeping for longer than an hour. Probably coincidence.

Okay, I'm gonna make the switches to the scritps.

---

### Post by quietglow on 2006-01-03
Well, I went all evening without a surprise shutdown but then it happened first thing this morning. 

I'm gonna delve into the scripts some more. I could seriously live without the powerbutton for shutting things down if removing references to it from the suspend scripts would keep this from happening.

---

### Post by tbw on 2006-01-03
[QUOTE=quietglow]Well, I went all evening without a surprise shutdown but then it happened first thing this morning. 

I'm gonna delve into the scripts some more. I could seriously live without the powerbutton for shutting things down if removing references to it from the suspend scripts would keep this from happening.[/QUOTE]

That's really odd?! It's been working great here for the last 2 days....

Now I'm afraid it isn't actually fixed.

---

### Post by quietglow on 2006-02-11
For the sake of completeness: I've recently upgraded to Dapper, and I haven't had an unplanned shutdown since. Don't know if it solved it or what, but I have an uptime of 3 days now with LOTS of suspends and no problems.

---

### Post by naught101 on 2007-09-19
I'm having the same problem on a Dell d410, running kubuntu feisty... it's really annoying. I'm using kpowersave. anyone actually figure this one out, or know of a relevant bug report?

---

