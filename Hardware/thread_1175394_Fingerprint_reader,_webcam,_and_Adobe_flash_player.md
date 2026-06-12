---
title: "Fingerprint reader, webcam, and Adobe flash player help needed."
date: 2009-06-01
forum: Hardware
---

### Post by TheNad on 2009-06-01
For refrence, I'm using a Dell Studio "17.

I'm new to the forums and new to Ubuntu (and Linux in general for that matter). Been using Windows since '95 but finally saw the light with my new laptop when I got the blue screen of death after less than a week of owning it. Anyway, did some research and decided on the Ubuntu flavor of Linux. I've installed the OS with no problem but I have a few questions. My main question is, is there any way I can get my fingerprint reader to work with any programs currently available?

Also, what is the best option for running my built in webcam? Any specific program favored?

I know this isn't a hardware problem but I didn't want to make a whole new thread for it... I'm also having trouble installing adobe's flash player for firefox (64 bit). I keep getting an error saying "Wrong architecture 'i386'" when I try to install the .deb file. Can I install the other files for Linux that are not specifically for Ubuntu or no? (link to the Adobe page: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/))

---

### Post by zerotre78 on 2009-06-01
Hi!
If you chose 64-bit just because your cpu have 64-bit extension available, let me suggest you to start with 32-bit ubuntu Jaunty 9.04. Im my experience is a painless install, you'll be able to run firefox+flash 10+ Java in minutes. For your webcam.. try to get familiar with "add application" in your gnome menu and add (if not already installed) "cheese". The best to play with your webcam.
Fingerprint reader support in my experience (I have one) is still under development and I didn't managed to use it.

Hope this helps,
Gianluca

---

### Post by zipperback on 2009-06-01
Software management is easy if you use an application like Synaptic.

System -> Administration -> Synaptic Package Manager

It will prompt you for your password.

Once you have started Synaptic, then you can search for the applications that you want to install.

For example, type the word flash into the quick search box, and then scroll down the list of applications that is brings up. Select "flashplugin-nonfree", and then click the apply button.

Wait a about a minute or so depending on your connection speed to the Internet, and then the plugin should be installed.

You can find a pretty helpful how-to document at the following link:

[http://ubuntuforums.org/showthread.php?t=766683&highlight=flash+player](http://ubuntuforums.org/showthread.php?t=766683&highlight=flash+player)

Hopefully this will help you.

- zipperback

---

