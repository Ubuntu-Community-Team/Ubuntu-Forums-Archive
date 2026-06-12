---
title: "Thinkpad R32 + Hardy Heron Issues"
date: 2008-05-06
forum: Hardware
---

### Post by Lorele on 2008-05-06
I'm a new Linux user.  I used Kubuntu on my laptop from the end of Feisty through Gutsy.  Then I switched over to Ubuntu.  I've had some issues which persisted from Kubuntu, but some of them are new, and some of them are gone.  I'm glad to have migrated, but I still need some help.

I don't know how to post my system specs or details from a prompt output.  I still haven't learned all the command line interface tools; I know I should, and I really don't know if there's a good primer on learning all the basic command line tools or what.  If someone could suggest me a place to start, it would be helpful.

I have a Thinkpad R32, with 1010.6 MB of RAM, and a Mobile Intel Pentium 4 - M CPU 2.00 GHz.  I think it comes with something like ATI Radeon Mobility 9600 M6 LY graphics on board or something like that.  I don't think I should be experiencing some of the problems I've been having, and I hope that by posting on here, someone will be able to help me.

--

Brief Synopsis

(1) My processor overheats way too often.  This can't be good for the processor, either.
(2) Rhythmbox starts skipping as a precursor, and can't manage to keep itself together when other processes start demanding attention.
(3) My sound system gives up after suspend and hibernate.  It doesn't want to come back.
(4) I also can't get sound to work nicely for Shockwave Flash or some games in WINE, even though it worked before.
(5) I'd love to find out how to make WINE appreciate the games I ask it to run; or at least to give me a normal-speed interaction.  Is this too much to ask?  Is there a way to do it?  Are there options to tweak?
(6) My home/.dmrc file still doesn't want to work nicely.  I have no idea how to resolve this, either.

--

So, first of all, my computer's been overheating.  I can't actually get a measurement or determine how hot it's running.  I just know that I have a fan which attempts to cool down my processor whenever I overburden it.  And when I say "overburden", I mean any and all of the following: running the package manager updater, opening Gmail in Firefox 3 beta 5, telling DeVeDe to create an ISO, or having more than 5 windows open at any time.

My first hint is that Rhythmbox starts skipping.  I thought Rhythmbox uses less RAM than Amarok, and it also preserves my playlists when it exits out.  But it skips when I start to do ANYTHING complex, and it continues to skip for several minutes if I don't do anything; I installed the taskbar music-applet widget, so at least I can hit "pause" when it starts to skip, but it's taken up to a minute or two sometimes just to register that I've clicked it.

Now, I know the Thinkpad was made for Windows -- and this may be simply a penalty for installing an OS that it wasn't designed for.  Not to say that it never overheated with Windows, but that it didn't overheat *as much*.  Now, it seems that it overheats and slows down when I tell it to do anything more complex than make a cup of tea.  Highly improbable.

Kubuntu never really had a problem with my sound system.  It seems that Ubuntu Hardy doesn't like it, though.  I can't even get Audacity to play sound, currently.  However, the bigger issue, is that sometimes, particularly when I suspend or hibernate the computer, when it comes back, it won't even attempt to play sound.  I googled and found information on how to restart the sound system as well as try to tell it to remember that I have a sound system when it comes back from suspend, but it doesn't seem to click.  When I did restart the sound system, the pitch was completely bent, and I had to just do a plain system restart.  This is very frustrating.

I also installed Shockwave Flash (the Adobe codec; I tried the other two, on the off chance they might work better, but no dice there).  Now I can get a visual, but it's very slow, and there isn't even sound when I go on to youtube.  I don't know what else to do about this.

I've also been using WINE and I don't know if there's a way to optimize it or make it run programs without trying to constantly access the hard drive on every little graphics update.  I tried running "Total Annihilation", and the sound on it has given out -- the first time I ran it, the sound was fine, and I managed to play a game without much trouble (although the Windows Emulator lags, in general)...  now the sound on it has given out, too.  I also miss playing Heroes of Might and Magic III, since it runs even slower (how?  it's not even a real-time strategy.) on WINE.  I'm thinking of making a dual-boot on here, but I don't know how to go about it without damaging my partition data.  I can't do it while booted from the hard drive.

I've also been getting a continual error on login (before login, really) that my HOME/.dmrc file is being ignored.  I've followed what it told me to do, and I've even followed some suggestions that I found by googling this error.  None of it seems to help, though, because the error still persists.  I don't know what to do about this.  I've tried chmodding and chowning, and it still doesn't have any effect.

---

### Post by jimv on 2008-05-06
About the temperature thing, there's a panel app you can add that will show you the temp of your CPU.

Open a command line and type

sudo apt-get install computertemp

When that's done, right click on one of your panels and click Add To Panel
Find the Computer Temperature Monitor and add it.
That will show you how hot (or not hot) your computer is running.

---

### Post by Lorele on 2008-05-06
Well, I performed the apt-get of computertemp, but it doesn't show up as something I can add to my panel.  Maybe I need to reboot.  I don't know.

Either way, that's only a drop in the bucket.  It's not going to solve anything -- it's just going to let me know how badly my computer is overheating.

---

### Post by Lorele on 2008-05-07
It seems to be defaulting to waver around 147 to 163 degrees Fahrenheit...  at normal pace...  "normal", that is.

---

### Post by Lorele on 2008-05-08
Someone's going to have to forgive me for bumping my own thread...  I've gotten one response.  I've followed the suggestion.  And now I'm still left with about a dozen other unresolved issues.

Doesn't this community pride itself on being able to help other users, and providing a strong support network?  I haven't seen it.  And without any sort of help or support, I'm beginning to lose some faith.  I know that I'm just one person, and I know that I'm probably one of the few who uses a Thinkpad with Ubuntu...

Am I posting in the wrong forum?

--

Let me describe the scenario that led up to today's frustration.

First, we know that my computer is doing fine for RAM.  I pulled up the gnome-system-monitor, and the most important thing it could tell me was that the gnome-system-monitor was using something around 30% of my CPU, rhythmbox was using something around 30% of my CPU, and python was using something around 20% of my CPU.  It's only using 303 MB of it's 1012 MB of RAM, so that's clearly not the issue here.

I was simply using Pidgin and letting Rhythmbox play.  You know, this isn't a high demand of a computer.  Really.  I wasn't asking it to perform complex calculations of pi.  Well, apparently, it considers even one instant message to be a bombardment worthy of causing the entire system to skip and nearly overheat.  And then, of course, my fan kicked on, and it overheated.  It seems to like to drive itself up to 168 degrees and then to cool itself down to somewhere around 152.

Meanwhile, the system monitor, which purports to be using 30% of my CPU, isn't responding when I simply click "close", and waited something around a minute or two (because the standard 10-second delay takes longer when the system is overheating) to even pop up a "Force Quit?" window.  Come on.  Seriously.  It's using 30% of my CPU, and is meant to take priority.  Why can't it respond to a "give me back some space" command and close itself with a minimal amount of that?

Of course, over the course of the next 10-15 minutes, I could not even get Rhythmbox, also purportedly using something around 30% of my CPU.  Not that it helped, because it was skipping to the point of giving me about a split-second of music for every 2 seconds of time.  And it wouldn't respond to the applet in the panel until after the next track came on; this was after about 10 minutes.  It finally did pause.  And in the mean time, I dealt with the computer not only playing horrendous skipping music, but also completely ignoring me.

The computer is obviously using its system time to do SOMETHING.  Why isn't it using its system time to respond to me and what I'm doing?  I'm the user.  This is seriously getting frustrating.  Nobody on these forums has any suggestions as to what to do?

---

### Post by droundy on 2008-06-22
I'm afraid I can't help any, but can reproduce the sound problem here on my thinkpad x22:  hibernation or suspend causes the sound to stop working.

I also find that when I suspend the backlight for my lcd screen remains on.

:(

---

### Post by wenuswilson on 2008-07-15
[http://ubuntuforums.org/showthread.php?t=786402&highlight=undervolt](http://ubuntuforums.org/showthread.php?t=786402&highlight=undervolt)

Reduction of Volts -- Reduction of extra heat.

---

