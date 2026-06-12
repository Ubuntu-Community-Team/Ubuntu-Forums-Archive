---
title: "Hardware lag after 1min idle"
date: 2008-05-12
forum: Hardware
---

### Post by tufkal on 2008-05-12
After about 1 minute of idle on my Heron install, my hardware lags.  

Here is a repeatable example.

I can open a terminal and type 'ping google.com'

And watch the replies, but after about 1 minute the replies stop.  Then I go to move my mouse to click something to figure out what is going on, and my mouse lags hugely from one side of the screen to the other.  Then after 5 seconds, my mouse works again, the pings restart, and im fine.  Note, I do not get failed ping messages, as the screen itself seems to just freeze at that point.

If I repeat this example with WiFi, i have to reconnect to the AP each time I have a 'hardware lag'.

Default install using alternate desktop CD on a Compal JFL92 laptop.  1 ext3 / partition, and 1 swap partition.  No restricted drivers installed.  

NOTE: Repeatable problem confirmed to be repeatable on first boot from install.

NOTE: This was first noticed doing apt-get installs of lots of data.  Ping is just a easily repeatable example.

NOTE: The mouse lag doesnt always happen, but the freeze always happens.  During top, watch date, or pings.

The odd part is the pings take up where they left off, with no large response time.  icmp_seq145, wait 5 minutes of freeze, and icmp_seq146 goes right off with normal response.

---

### Post by tufkal on 2008-05-13
Shameful self-bump.

---

### Post by Stefan Stryjecki on 2008-05-13
What is a "self-bump"?

I don't know what can be the cause of this. It makes me a little worried actually, b/c I planned on buying a Compal JFL-92.

---

### Post by tufkal on 2008-05-13
Are there any other JFL92 laptop users that can chime in on this?  I mean, it is such an obvious problem, and can be seen on first boot from install, just doing a apt-get upgrade.

---

### Post by zolushka on 2008-05-14
I have a Dell Latitude D600 that had been acting in a similar way since installing Hardy. (Before that it ran Debian etch with no such problem.)

About an hour ago, after discovering that the GNOME panel's "Laptop Brightness Applet" causes the laptop to lag like crazy, I tried the following things:

1) In the "Power Management Preferences" dialog, I disabled the "Dim display when idle" settings.

2) Using gconf-editor, I disabled the "ambient" and "backlight" settings under /apps/gnome-power-manager

I wasn't scientific about it, so I don't know which of those changes did the trick (the gconf tweak probably wasn't useful at all).

But so far, so good...

There, I suppose I'll jinx it now by posting this message ;^)

---

### Post by tufkal on 2008-05-14
I'll give that a try right now and let you know the results.

---

### Post by zolushka on 2008-05-15
So far everything's still running smoothly for me, and it's been almost a day...

---

### Post by tufkal on 2008-05-16
Havent had a chance to test this yet, but in some quick tests last night it appears a newly pushed update might have fixed it for me.

I'll have more tomorow.

---

### Post by tufkal on 2008-05-16
Yeah that doesnt help.  Those settings under power managemanet are all turned off by default when plugged into AC anyways, so changing them would make no difference.

I guess it could be the gconf changes you made, I will test some more.

---

### Post by tufkal on 2008-05-16
I am beginning to think it is the kernel itself...

I found this....

[http://groups.google.com/group/linux.kernel/browse_thread/thread/fbb680f555065eda](http://groups.google.com/group/linux.kernel/browse_thread/thread/fbb680f555065eda)

It looks like some commits to the kernel were made very recently to add support for acpi and other things for the IFT00 boards from Compal, including the JFL92.  (Can someone confirm this?  Havent read a diff file in a long time, and never from the linux kernel)

If this is the case, looks like to use Heron on a Compal JFL92 im going to need to recompile my kernel?

---

### Post by tufkal on 2008-05-16
God this is driving me nuts....just browsing the web to find a solution to this problem, I keep getting tiny screen freezes like described above, and seconds later, my WiFi connection stops working and I have to reconnect to my AP.  

So then I plug in my LAN connections, and I dont have to reconnect, but Pidgin keeps having to relogin ever time i get a lag, and the lag itself is beginning to become annoying.

Can someone please help me here?

---

### Post by mdhooge on 2008-05-16
I have a Dell 630m with the same kind of misbehaviour. I tried several things without success (e.g. with & without compiz, powered & on battery, ...). The only thing that seemed to work was to load the CPU to 100% (for instance with an ugly javascript from a website).

> **zolushka said:**
> 
1) In the "Power Management Preferences" dialog, I disabled the "Dim display when idle" settings.


I change the power-connected tab and it seems to do the trick... crossing fingers.

---

### Post by tufkal on 2008-05-17
On my install, under the AC power connected tab, that option is allready turned off....so what did u change?

---

### Post by mdhooge on 2008-05-18
Well, it was on and since I switched it off everything seems to be better. But I've never been really sure on the way to trigger the problem. So maybe the trick is only valid for dell laptops.

What puzzles me is that I never found what component did the lag. I checked the CPU freq, the logs, everything I could think about... with no result.

---

### Post by swarley-barney on 2008-10-21
Hey guys.

I also have the same problem but with a fujitsu siemens laptop. I have recently installed Kubunto 64bit on it but can't find a soulution for that anoying lags. Anybody has some new ideas besides the desktop dimming, because that doesn't work for me :/

---

