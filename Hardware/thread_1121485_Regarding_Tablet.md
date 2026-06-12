---
title: "Regarding Tablet"
date: 2009-04-10
forum: Hardware
---

### Post by Nir Friedman on 2009-04-10
So, I just received my new laptop. It is an x61 Thinkpad tablet, which I got for very cheap (650) because I think Lenovo was trying to get rid of them all. I played around with it today, the computer is phenomenal in terms of all around build quality, size is perfect, tablet has a great feel.
My original plan was to wipe vista and install kubuntu. But now I feel a bit more hesitant for two reasons. First off, vista isn't nearly as horrible as I was led to believe, although I'm sure some things will start to piss me off shortly. Secondly, the level of tablet integration into vista is fantastic and it will make me sad to give that up. The handwriting recognition works incredibly well, its basically perfect if you print and even with cursive its not bad, and I'm sure if I actually trained it it would get better. Anytime you click on a field while you are browsing, the tool to enter handwriting automatically has an icon appear. All in all its very well done and it becomes extremely tempting to use it as a tablet when you are surfing the web and not typing much. 
I know that Ubuntu has some degree of support for tablet, but I'm sure it will not nearly as good as this. From what I've seen of tablet apps in Linux, it seems like a smattering of older projects that had potential but are now deprecated, newer things that cover some niches, and things that just don't work as well as their windows equivalent. Also the overall integration into the OS seems much less.
Anyone have experiences using tablets in both OS's that can give me some suggestions? I want to have Linux firstly because of preference for the OS, and secondly a lot of my work is programming and such and I prefer to do that in a Unix environment. I really want to take this step of wiping the computer but I feel a little inhibited still, so some honest appraisals would be appreciated.

---

### Post by Favux on 2009-04-10
Hi Nir Friedman,

I agree with you and I dual boot.  The main problem with linux is limited handwriting recognition.  That said there are great programs, depending on what you want to do.

This link may help you with installing Intrepid:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_X61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_X61)

---

### Post by Nir Friedman on 2009-04-10
Although this appears useful, it seems that this is referring to the non-tablet version. I don't know to what degree the two computers are identical or not aside from tablet functionality, so we'll have to see I guess. I hope however that my laptop works a bit better with Ubuntu then what is reported here, some of these problems are a bit brutal.

---

### Post by Favux on 2009-04-10
Hi Nir Friedman,

My apologies.  It's usually easy enough to set up Wacom features.  What version of Ubuntu are you planning on installing?

---

### Post by Nir Friedman on 2009-04-10
I was going to go with the latest release of Kubuntu. If something that was beta is getting a final update I'll probably wait until that happens. I'm still not sure whether to leave Vista or not, some parts of it are really annoying me already. It's a shame windows 7 isn't out yet, it looks much better. After I start the process though I'll probably be back here posting with specific things though, and then at the end I plan to write the whole thing up for the testimonials board.

---

### Post by Favux on 2009-04-10
Hi Nir Friedman,

Here is the link I meant to give you:  [https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadX61T](https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadX61T)
it also has another link.  The only thing I would do is not use the "cursor" section or "cursor" in "ServerLayout".  This is a common mistake, the cursor is for the Wacom mouse which your tablet obviously does not have.

The link is for Hardy but should work for Intrepid.  With Jaunty xorg.conf configuration will probably not be an option.  Instead it will be HAL and the 10-wacom.fdi file with it's dBUS callout to get the Wacom input devices.  Massive changes occuring just in the last few days.  No idea of how the dust will settle.

---

### Post by Nir Friedman on 2009-04-12
Hmm I was actually just planning to wait for the release of Jaunty to install it onto my tablet, but now I'm wondering if this is a bad idea since people will not know how to get tablet functionality working. I was hoping that jaunty would have better support for this kind of stuff since I find that on the whole ubuntu takes big step forwards at every release when it comes to support. Do you have any suggestions based on your experiences? Should I go with 8.04, 8.10, 9.10 beta or wait until 9.10?

---

### Post by Favux on 2009-04-12
Well at this point it looks like you can go to Jaunty and by compiling the 0.8.3-2 and using the "old" xorg.conf method get functioning Wacom.  At least two users have managed it for 9.04.  So given that there isn't much difference between 8.04, 8.10, or 9.04 beta regarding Wacom.

If you go here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  there is more information in the Jaunty announcement near the top.  If you follow the link to near the end of the thread there is more information regarding the new HAL/.fdi dBUS method.  Also some links to other relevant threads and launchpad bug reports as you go forward in the thread.  Of course the newer the version the newer the kernel with the usual improvements that brings.

---

