---
title: "Toshiba Satellite A135-S4487"
date: 2008-10-31
forum: Hardware
---

### Post by -kg- on 2008-10-31
This is not a call for help (yet)...I just wanted to give a big thumbs-up to the Ubuntu development team and all who have done so much work on the Ubuntu distros. Too bad you don't have a Thumbs-up smiley...you need to include one, so here's five of them: [IMG]http://img.photobucket.com/albums/v634/kg5uc/coolthumb.gif[/IMG] [IMG]http://img.photobucket.com/albums/v634/kg5uc/coolthumb.gif[/IMG] [IMG]http://img.photobucket.com/albums/v634/kg5uc/coolthumb.gif[/IMG] [IMG]http://img.photobucket.com/albums/v634/kg5uc/coolthumb.gif[/IMG] [IMG]http://img.photobucket.com/albums/v634/kg5uc/coolthumb.gif[/IMG]

I have installed 8.04 on my desktop (a homebrew AMD-64) and now my laptop, which is, as the title of this post says, a Toshiba Satellite A135-S4487.  This was one of Toshiba's models that originally made for and shipped with Vista.  I bought it a couple of days after Vista was officially released (Best Buy told me that they had been holding them back until the official release date...they had had them in stock for a while before that).

On my desktop I had (and still have) a few minor problems, such as no system sound (the players all work) and such, but as far as I can tell, everything in the installation on this laptop works ***flawlessly!***  I haven't checked *everything* out (I don't know whether the DVD burner works yet), but everything else works without a hitch.\\:D/

When I first tried the LiveCD in the laptop, I was disheartened because, unlike the desktop, I couldn't connect right up to the internet via my wireless connection.  On the suggestion of a friend I downloaded the ISO for FreeSpire, because he said that FreeSpire/LinSpire had extensive wireless support.  The very first problem I ran across was the EULA at bootup to the LiveCD...not *FREE!*  While I expect to be forced to use a few non-free drivers and am not *totally* opposed to using a few non-free codecs and the such, I *at least* expect the Distro to be free!

The second problem I encountered was that I couldn't get the sound to work whatsoever.  Nothing I could do would give me any sound at all.  The wireless was supported, but I still didn't have internet access.  The only thing I could say about FreeSpire is that I discovered *why* I couldn't connect to the internet.  When I originally popped in the Ubuntu Live CD, I checked for internet access by launching Firefox, just as I did on my desktop (through which I had instant access).  I had forgotten that, while the desktop is wired directly to my DSL modem via Ethernet, I am more than computer literate enough to have set up WEP encryption on my wireless.  Of course I couldn't connect through the wireless...I hadn't entered my WEP Hex key!

Since I was pretty well convinced that I didn't want to install FreeSpire (a non-free EULA?!), I popped in the Ubuntu LiveCD to see if maybe it had supported my wireless all along.  And it did!  Same problem, of course...no encryption key, no access.  I attempted to put the key in, but it didn't seem to want to accept the key, so I figured that was probably because it needed somewhere to store the key (like a hard drive location), so I shrank my Vista partitions and installed.

Sure as shootin', I brought up the Ubuntu installation, configured the wireless connection, and up it came.  Up came everything else, as well.  Full and total system sound...everything, as far as I can tell and as far as I've tested.  USB support (I have a USB trackball and a USB ergonomic keyboard which both work perfectly), video support (without any non-free drivers, which I had to have for my desktop with an nVidea card...3D acceleration driver was non-free), wireless support (a *big* plus, and the major thing I was worried about), and all.  Like I said, I have yet to test the DVD burner, but I have no doubt that will be supported as well.

I'm now running the remaining BOINC work units off of the Vista installation (Seti@Home, and I have one Astropulse and a few regular to go) then will disconnect under Vista, install the BOINC client under Ubuntu, and start the crunching there.  I *do* have one question (which I will find out once I start BOINC under Ubuntu, but what the heck):

How well does Ubuntu support multi-core processors?  This laptop has an Intel duo-core processor.  When I run my BOINC client under Vista, it does two work units simultaneously, which obviously will be twice as fast as with a single core processor.  Can I expect the same under Ubuntu Linux?

I'm an old hacker from way back in the DOS days (before there was Windows...I remember seeing Windows 1.0 on the software shelves and thinking, "Oh great...another DOS shell.").  I kept up with it through all the DOS and Windows versions, with Windows becoming harder and harder to "hack"...it was getting to be no fun.  I had brief forays into other OSes...OS2, BeOS, Atari (I had a couple of Atari 800XLs for a while), and yes, even Linux in it's earlier days.

Now I think I've found a new home.  Linux is very configurable, "hack-able," and seems like it's going to be fun to play with (as soon as I get this "learning curve" thing behind me!).  Kudos where kudos are due!  Once again:   [IMG]http://img.photobucket.com/albums/v634/kg5uc/coolthumb.gif[/IMG]

Thanks Guys and Gals!

---

### Post by rajan on 2008-11-14
moving from windows to linux of any type will be better for running boinc. they're out of UC berkeley (i think) and that's where the BSD kernel came from (which is now apple's foundation). in my installation of boinc under windows, it was a pain and occasionally unstable. linux is what i presume BOINC was written for in the first place because it was much easier to install on ubuntu when i switched over (and for the reasons above). the gui isn't as great, but whatever. as for parallelization, i'm not sure BOINC needs your processors in parallel (that is, they don't need to communicate). i know when i was using another distribution of linux (red hat), it was trivial to get both processors going with two separate programs. however, a program would need to be well-tailored to your system in order to use the processors in a way that would be beneficial.

welcome to the forums, and it's good to see that you're getting along well so far.

---

