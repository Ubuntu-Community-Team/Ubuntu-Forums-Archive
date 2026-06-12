---
title: "Asus 1201N wireless need help"
date: 2010-02-07
forum: Hardware
---

### Post by Rumbl3 on 2010-02-07
Well I'm a bit of a noob when it comes to drivers etc.

How do i go about installing the wireless on this netbook? i just installed 9.10 fresh haven't dont anything so i need the steps how to get the wireless working.

Thx

---

### Post by pi/roman on 2010-02-07
[http://ubuntuforums.org/search.php?searchid=69855962](http://ubuntuforums.org/search.php?searchid=69855962)

---

### Post by Rumbl3 on 2010-02-08
When i click that link just says sorry no matches. But i'm guessing just search the forum here?

---

### Post by pi/roman on 2010-02-08
Sorry, the link died, here is a new one:
[http://ubuntuforums.org/showthread.php?t=1388727&highlight=1201N+wireless](http://ubuntuforums.org/showthread.php?t=1388727&highlight=1201N+wireless)

---

### Post by Rumbl3 on 2010-02-08
At the end of it, it says not to update to 9.10? So do i follow those steps still anyway? LOL sorry for being a noob I been away from ubuntu for a long time and just finally got this netbook about 5 days ago. Relearning all over again.

Btw I see something about not testing the wifi, my regular ethernet works just fine right now.

UPDATE
 found this on newegg's reviews of the netbook i got. 

POSTED by Neuro on newegg review for 1201n

wireless in linux 


Pros: got mine running ubuntu 9.10.

Cons: wireless nic does not work out of the box in linux. to the best of my knowledge this applies to all distros.

Other Thoughts: download the rtl8192se_linux_2.6.0010.1211.2009.tar.gz driver.
tar it. cd into that directory. su to root. then "make" and "make install". after that you should be good to go. 

So when I get home I guess i'll go to town see if i can get it working.

---

### Post by CarlGWatts on 2010-02-17
Hey Rumbl3: Did the suggestion of installing the rtl8192 thingy work?
Does that seem to be the best way to get WiFi working on the ASUS 1201n on Ubuntu 9.10?

---

### Post by Joshisfloyd on 2010-02-24
The suggestion worked for me fairly well. The initial "make install" failed, but was successful as soon as I took full root with sudo su.

Unfortunately, it failed within a few days. Now it flickers between on and off. I'm going to try a make clean since it seems to have broken after updating the OS.

Update: After remaking and installing the drivers, the wireless works beautifully. I am still searching for a longer term solution, but at least I can fix it if it breaks again.

---

### Post by hsoulen on 2010-04-07
> **Joshisfloyd said:**
> The suggestion worked for me fairly well. The initial "make install" failed, but was successful as soon as I took full root with sudo su.

Unfortunately, it failed within a few days. Now it flickers between on and off. I'm going to try a make clean since it seems to have broken after updating the OS.

Update: After remaking and installing the drivers, the wireless works beautifully. I am still searching for a longer term solution, but at least I can fix it if it breaks again.

Hi there.

My best advice for Karmic (9.10) is check the Realtek site for the most recent driver "rtl8192se_linux_2.6.0015.0127.2010" is the latest.

Do not unpack the archive to the desktop as this causes problems with compiling the driver, unpack it to something like "~/Drivers" then run the following:

cd rtl8192se_linux_2.6.0015.0127.2010
sudo make
sudo make install

You can also remove the driver with "make uninstall" from the same directory should you need to.

You will need to re-make the driver every time you install a new kernel (bit of a pain) but wireless works very well with this driver.

I am running the Lucid (10.04) Beta 1 at the moment and although the driver is built into the newest kernels for Lucid they still don't work well or at all, hoping the final release at the end of the month will have it working. Until then I am still using the Realtek native driver and its working well.

One note, suspend works about 50% of the time with this driver.

Hank.

---

### Post by tarehart on 2010-05-27
The above worked great for me, thanks!

Here's a link toward the driver: [realtek.com/downloads/downloadsView.aspx?blahblahblah]("http://www.realtek.com/downloads/downloadsView.aspx?PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192SE")

---

### Post by neurotopia on 2010-08-05
ROFL... i'm the dude (aka neuro) that posted the fix on newegg and totally FORGOT about that solution!  i was doing a fresh 10.04 install and found this thread googling for a fix.  i don't know if that's sad or funny... or a little bit of both.

---

