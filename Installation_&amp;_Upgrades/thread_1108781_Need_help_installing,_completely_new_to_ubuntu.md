---
title: "Need help installing, completely new to ubuntu"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by Shukero on 2009-03-28
Hello everyone! I just transitioned over to Ubuntu from windows and it is definitely a wake up call since I've never had this much trouble trying to install something before.

Here is what's happening:

I am trying to install this theme:
[http://www.gnome-look.org/content/show.php/StarDust+Pack?content=101468](http://www.gnome-look.org/content/show.php/StarDust+Pack?content=101468)

But to install that I need to install GTK+....
BUT to install that I need to install it's libraries...
B-U-T before I install that I need to install pkg-config...

(P.S. If anyone could find me a better way of installing this PLEASE PLEASE tell me!!)

Now that I've said that, I've gone through the "./configure" and the "make", but when I get to the "make install" I get a "cannot create permission denied general file usr/local/bin/pkg-config access denied"

Can someone help me out by telling me what I'm doing wrong?? I've been trying this for hours >_<

---

### Post by infinitejones on 2009-03-28
Type sudo make install, not just make install

You need root access to do make install, and that's what the command sudo gives you. It'll ask you for a password, which is the one you use to login.

---

### Post by Shukero on 2009-03-28
Is there any easier way of installing this software? I went to synaptics install manager and installed all of the libraries, and when I went to ./configure GTK+2.14.7 I got a series of sentences saying Packages: Glib, Pango, and ATK not found.

I just want a theme to work \(>_<)/ 

can anyone help me here? I read in the install something about using pkg-config but I don't know how to use the terminal that well so if some one can help me with step by step it would be very helpful!

---

### Post by oldos2er on 2009-03-28
You picked a doozy of a theme to install, for a beginner. Maybe try something a bit easier? Most themes can be installed by dragging and dropping into the Appearance preferences theme window.

 If you're determined to install StarDust, here's some help:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by malfindin on 2009-03-28
I'm not new to Ubuntu, but I am new to posting. This will be my second. I agree with the last post in this message completely. You picked a hard one to start with. Some things to know.

1. If you want to install anything like this, use the Synaptic Package Manager, it usually catches any dependencies, especially if you check "consider recommended packages as dependencies" (In the preferences). It would be best if you read the entire Synaptic manual before continuing. Lots of cool things in there you want to know about. (mark by task is a fav)

2. Changing your theme also changes you theme manger(sometimes); and there are a bunch, Emerald, Metacity, ( the default if you just right click on your desktop), QT4, Kwin, KBFX, etc... Some only affect certain apps written in certain languages, some affect all your settings. It's one of the true areas where things can get more complicated than MS Windows, but here is the catch--only if you let them. The defaults are better and easier than Windows and really never need to be enhanced that much.

3. I use Emerald as a theme manager, Compiz Fusion for desktop effects and only Emerald theme's and I think you would be stunned to see how pretty my computer is.

I believe you can see my screen shots if you look up my user malfindin.

Bottom line Installing Theme's can get you into trouble and even crash your x-server, so wait until you know how to back out in terminal before messing with it or at least create an emergency admin user you can boot to in case your primary login is hosed. If you don't know what "crashing you x-server means" think no GUI--text commands only at a DOS like prompt. It's always there in the background if you hit ctrl+alt+F1.

Hope this helps, oh and if you do it anyway. Post your success, I'm sure we would all like to know how it turns out.

malfindin

---

### Post by magalia95954 on 2009-03-29
[LIST]
[/LIST]I am drowning with this new linux laptop I am a pc user I need some help please

magaila95954

---

### Post by 3rdalbum on 2009-03-29
The installation process that you are going through is not to install the theme - it's to install an experimental bleeding-edge version of a "theme engine" that is required in order for this bleeding-edge theme to work. In addition you're not just "installing" the software, you are compiling it from its source code. Hey, it's bleeding-edge software.

There are plenty of similar themes on Gnome-look.org that only require you to drag the .tar.gz archive onto the Appearance window; maybe try one of those?

---

### Post by malfindin on 2009-03-29
Well I might have gone a little softer than 3rdalbum on a newbie and used the phrase Bleeding edge less, but he's giving you outstanding advice. You see you aren't comparing apples and oranges, you are comparing apples and a custom ultra-light plane kit (some assembly required). You might think that Linux is harder than Windows, but nothing could be farther from the truth. To do the same in Windows would take:

1. A couple thousand dollars in software.

2. Several months of programing school.

3. I think a developers license (or some such thing) from MS.

4. And no life.

If you stick to the Metacity theme generator you can make one yourself in minitues.

The fact that someone as new as yourself can even download and attempt to compile Bleeding edge (OK I lied, like the expresion to) software is the miracle that is Linux/Ubuntu.

Rejoice and be merry, for tomorrow you might have to use windows again.

Everything new takes some time to learn, but I can assure you beyond any shadow of a doubt that if you were new to computers in general Linux is far easier to learn, lighter on the wallet, nearly maintenance free, oh and lets not forget better looking than windows ever thought of being. Just give it time.

malfindin

---

### Post by yeats on 2009-03-29
> **magalia95954 said:**
> [LIST]
[/LIST]I am drowning with this new linux laptop I am a pc user I need some help please

magaila95954

Hi there, 

If you need help, you'll want to start a new thread with your specific questions.  If you're completely new to Ubuntu, try posting in the Absolute Beginner Talk forum:
[URL="http://ubuntuforums.org/forumdisplay.php?f=326"]
http://ubuntuforums.org/forumdisplay.php?f=326[/URL]

---

### Post by malfindin on 2009-03-29
One last thought. Looking over all the replies you have gotten, the overall theme is a negative one and we have failed to "solve" your problem, other than to try to discourage you from attempting such an advanced theme.

**This goes out to all the moderators and admins out there.**

Discouraging a newbie in this case might be the best advice, but it is not what he asked for and I believe the purpose of these forums is to encourage Ubuntu use, not discourage it.

Could someone with a tad more terminal command experience than I please step in and give this fine struggling new Ubuntu user the theme he wants. Even if it is hard, I would like to know all the steps myself to installing it from scratch.

And then we can sit back and quietly muse to ourselves why a PC user wanted a theme to make his Linux computer look just like a MAC. Perhaps it is one of the seven great mysteries.

To quote someone far better than myself, "Our is not to questions why, ours is but to do or...not post in the Ubuntu forums"

Good luck, and feel free to personal message me. I'm a little more verbose than the average poster. Also when you post a question such as this one it helps to state why you are trying to do something along with the things you are trying to do. For instance, if a bet was riding on your geting this theme up and running, etc...

best wishes,

malfindin

---

### Post by yeats on 2009-03-30
> Discouraging a newbie in this case might be the best advice, but it is not what he asked for and I believe the purpose of these forums is to encourage Ubuntu use, not discourage it.

I think it's good advice in general to steer new users back towards the repositories and away from installing from source, at least until they get a better understanding of how the system works and why it's built the way it is.  This is not discouraging use so much as it is educating a newbie about alternative ways to do what she/he is trying to do.  I generally go by this from the [policy page]("http://ubuntuforums.org/index.php?page=policy") (section II, #14):

> Please remember to do things the Ubuntu way. There are always more than one solution to a problem, choose the one you think will be the easiest for the user. Automatic package installation (using Synaptic, Aptitude, or apt) over manual installation. DEB over source. Please never instruct users to do anything that might break their system, this includes using --force and -ignore-depends when installing a DEB. Try to think as a green user and choose the simplest solution.

I'm sure that's where our fellow posters here are coming from :-).

---

### Post by fballem on 2009-03-30
> **chrissharp123 said:**
> I think it's good advice in general to steer new users back towards the repositories and away from installing from source, at least until they get a better understanding of how the system works and why it's built the way it is.  This is not discouraging use so much as it is educating a newbie about alternative ways to do what she/he is trying to do.  I generally go by this from the [policy page]("http://ubuntuforums.org/index.php?page=policy") (section II, #14):



I'm sure that's where our fellow posters here are coming from :-).

To the Original Poster - I've been using ubuntu for nearly a year now, quite happily. There is enough new things to learn about a new operating system and new software (I used Windows since Windows 3.1). Compiling themes - especially the one that you chose - is not for the faint of heart. My suggestion, if I may, would be to select a simpler theme, from the thousands available, and use that for now.

In the meantime, there are a number of websites, such as this one: [http://orford.org/gtk/](http://orford.org/gtk/) that explain how gtk themes work. By the way, gtk themes (used during a session after login) and gdm themes (used during login itself) are different and are put together differently.

Welcome to Linux and welcome to Ubuntu.

---

### Post by malfindin on 2009-03-30
@chrissharp123 No arguments there. I stand corrected. To quote Kirk, "you keep right on quoting those rules." I did not remember that one, and as a brand new poster I really appreciate advice like this more than I can say. Linux/Ubuntu is now quite literally my life and my job now. In the year or so I've been using it I hadn't "given back" yet and helping out here in the forums is my way of paying for the best OS I have ever seen or even heard of.

@fballem Thank you for the info about GTK and GDM...I did not know that. Oh and I want your desktop wallpaper. Is there a way to email to me?

@Shukero--The original poster. I know what's it's like when you want something and can't get it, but these folks are telling it to you straight. Don't bite off more than you can chew this early on or you make your Ubuntu experience hard when it could be easy. I still remember what sold me on it. Perhaps it will inspire you.

A friend service tech at my hardware vendor gave me an Ubuntu 8.04 disk to check out. I got back to my company's shop and poped it in a new-build PC. During the install process I was distracted by a client's tech-support phone call. After getting off the phone, I walked back to the sys and the only driver missing, was the video card. 1 reboot later I was done with the install. I spent the next 2 hours trying to figure out which one of our other techs had searched for and downloaded all the drivers for this computer; I was mad someone had messed with MY PROJECT--and I think you know how this ends--only to find out no one had touched it. It was just that easy!!!.!!!

I then spent the better part of the day searching for VISTA drivers for a single PC and it wasn't long after that, that I decided to leave MS behind me and become a full-time Linux tech.

100% true story--hope you liked it.

Sincerely,


malfindin

---

### Post by fballem on 2009-03-30
> **malfindin said:**
> @chrissharp123 No arguments there. I stand corrected. To quote Kirk, "you keep right on quoting those rules." I did not remember that one, and as a brand new poster I really appreciate advice like this more than I can say. Linux/Ubuntu is now quite literally my life and my job now. In the year or so I've been using it I hadn't "given back" yet and helping out here in the forums is my way of paying for the best OS I have ever seen or even heard of.

@fballem Thank you for the info about GTK and GDM...I did not know that. Oh and I want your desktop wallpaper. Is there a way to email to me?

@Shukero--The original poster. I know what's it's like when you want something and can't get it, but these folks are telling it to you straight. Don't bite off more than you can chew this early on or you make your Ubuntu experience hard when it could be easy. I still remember what sold me on it. Perhaps it will inspire you.

A friend service tech at my hardware vendor gave me an Ubuntu 8.04 disk to check out. I got back to my company's shop and poped it in a new-build PC. During the install process I was distracted by a client's tech-support phone call. After getting off the phone, I walked back to the sys and the only driver missing, was the video card. 1 reboot later I was done with the install. I spent the next 2 hours trying to figure out which one of our other techs had searched for and downloaded all the drivers for this computer; I was mad someone had messed with MY PROJECT--and I think you know how this ends--only to find out no one had touched it. It was just that easy!!!.!!!

I then spent the better part of the day searching for VISTA drivers for a single PC and it wasn't long after that, that I decided to leave MS behind me and become a full-time Linux tech.

100% true story--hope you liked it.

Sincerely,


malfindin

wallpaper can be found here: [http://www.freewallpapers.tk/2007/01/abstract-neutron-revolver.html](http://www.freewallpapers.tk/2007/01/abstract-neutron-revolver.html)

I use it as the background for when I use nimbus theme, which works really well. Having said that, I like the new ubuntu theme in Jaunty, so I haven't been in a huge hurry to change it.

---

