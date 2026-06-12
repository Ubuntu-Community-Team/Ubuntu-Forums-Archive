---
title: "Ubuntuguide's sound solution"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by jzietman on 2005-06-25
I am one of the many people unable to hear any sound in ubuntu from my sb live! 5.1 sound card.  how many people have tried the solution offered on ubuntuguide.org?  I have still not installed ubuntu to my hard drive, and instead use a livecd (i386 version), and the solution requires a reboot making it useless for me.  

does this solution generally work?  i don't want to go to the bother of installing ubuntu (and getting it to boot how i want it, which is, by the way, the go to xp automatically and only even think of going to ubuntu if a special floppy is inserted at boot; that's how my friend does it with slackware; if you know how to do this with ubntu, please say) if i won't have any sound. 

so, if people can reply with their model of sound card and whether the solution ( [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly) ) worked for them.  

thanks!
jzietman

---

### Post by andlinux21 on 2005-06-25
I just installed Ubuntu to my home PC if you message me I can give you the specs when i get off work.  However my sound is working fine I didnt have sound
when I did the laptop install. On the desktop everything seems to work fine except trying to get my dialup working for my internet connection right now its set for my ethernet card. ](*,)

---

### Post by phantom on 2005-06-25
> **jzietman]I am one of the many people unable to hear any sound in ubuntu from my sb live! 5.1 sound card.  how many people have tried the solution offered on ubuntuguide.org?  I have still not installed ubuntu to my hard drive, and instead use a livecd (i386 version), and the solution requires a reboot making it useless for me.  

does this solution generally work?  i don't want to go to the bother of installing ubuntu (and getting it to boot how i want it, which is, by the way, the go to xp automatically and only even think of going to ubuntu if a special floppy is inserted at boot said:**
> http://ubuntuguide.org/#configuresoundproperly[/url] ) worked for them.  

thanks!
jzietman
 That's the way for asking support, we're all rushing to help you.

1. You didn't even install Ubuntu and you're complaining already
2. You do want to install, but using a boot manager is already to much for you
3. Did you even try to find a solution? The way the community works is that everybody does his part of the job, so do yours and stop relying on others.
It's not only taking because it's free, you're kindly requested to give something back.
4. If it works on Slackware for your friend, then go with Slackware
5. If I know that a distro is going to give me grief upfront, then I look for another distro, why not try Mandriva, the SBLive 5.1 works fine there.
6. My Audigy2 NX worked out of the box on Ubuntu.
7. Review these points, re-think your question and come back to us. Everybody is willing to help, but not this way.

Sorry if I was rude.

Have a nice day, and hopefully Linux will turn out right for you.

---

### Post by foxy123 on 2005-06-25
[QUOTE=phantom]That's the way for asking support, we're all rushing to help you.

1. You didn't even install Ubuntu and you're complaining already
2. You do want to install, but using a boot manager is already to much for you
3. Did you even try to find a solution? The way the community works is that everybody does his part of the job, so do yours and stop relying on others.
It's not only taking because it's free, you're kindly requested to give something back.
4. If it works on Slackware for your friend, then go with Slackware
5. If I know that a distro is going to give me grief upfront, then I look for another distro, why not try Mandriva, the SBLive 5.1 works fine there.
6. My Audigy2 NX worked out of the box on Ubuntu.
7. Review these points, re-think your question and come back to us. Everybody is willing to help, but not this way.

Sorry if I was rude.

Have a nice day, and hopefully Linux will turn out right for you.[/QUOTE]

the guy just asked if the solution works for anyone to avoid hassle installing Ubuntu and then find out that it does not. I do not think he cares about your Audigy2 in that case.

---

### Post by phantom on 2005-06-25
If it is known not to work in Ubuntu then you 2 choises:

1) Take another distro.
2) Try to find a solution and help others with it.

If there was a solution and it didn't work out for him then I would be happy to debug it with him.

As an example, I'm trying to get bluetooth input working, there is nothing about it in the guides, positive or not, I asked on this forum is somebody got it working yet, in the meanwhile I'm trying to get it working to help others.

Anyway, sorry if my 1st reply was not clear, the heatwave over here didn't help me in getting a good night sleep, I was in a bad mood  :oops:

EDIT: Regarding my Audigy, he might not card, but as that card is on a newer chipset then his there would be a major chance in his chipset being supported. I just gave that as an indication, nothing else.

---

### Post by jzietman on 2005-06-25
[QUOTE=][/QUOTE]
 Please phantom, there is no need to be blatantly rude.  I have been reading and asking questions on this forums and linuxquestions for months to try to find the solution, and I haven't found one that has worked for more than two people to make me feel like installing ubuntu won't be a waste of my time.  

I am using the livecd to make sure that the system is ok with all of my hardware. It works exactly like an installed copy of the distro. If I can get the sound to work in there, I will install ubuntu. 

My specific requirements for the bootloader are because I am obliged to share my computer with my mum so that she can use a vpn to do work at home.  She gets very worried/scared/upset at seeing the slightest change in the computer (she's not very techy ;) ), and changing how to computer boots would get her really confused. I know it would be simple to teach her, but it will really get on her nerves. 

Thanks, 
jzietman

---

### Post by sanji on 2005-07-20
Dear Phantom and others,

Its hurt when people ask you a "IQless" question (its because we are higher then them in that knowledge and in bad mood too). But believe, they are try to act kind. So do we(sometime), when we need people. Actully, its good to hear/read the question and people need to be mad(to make them right!). Majority, i'd agree with you!

Someone know how to hear a sound on Intel D915GAV motherboard? - Sound on board. :-?

---

### Post by tomchuk on 2005-07-20
Back on topic...

jzietman, if you cannot hear sound at all, using dmix will not help the situation. dmix is a module built into ALSA to allow pseudo hardware mixing instead of using a sound server like esound or arts. If the card was working you wouldn't need dmix anyways, as the emu10k1 driver for the SB Live supports the hardware mixer on the card. However, I find it odd that you're not gettting sound out of the box with an SB Live, as it is probably one of the best supported cards in Linux; Even though the SB Live is fundamentally broken and does not comply to the PCI spec.

If you could post the output of lspci and lsmod in [code] blocks, it would help us to diagnose your problem. It could very well be that the hardware detection on the LiveCD (which, IIRC is a little less sophisticated than that of a full Ubuntu install) is just not loading the right modules for your hardware - which would be a very simple fix.

Edit:
About the boot issue, you can have grub default to windows by changing the default parameter in /boot/grub/menu.lst. Your mom would have to endure a couple extra seconds, but would not have to make any choices from a menu or even look at anything too out of the ordinary. All you'd have to do is press escape during boot to get the grub menu and choose Ubuntu. This is far preferable to boot floppies, as they can easily be lost, broken or corrupted which will create a bunch of work for you to get back into Ubuntu.

---

### Post by mjkelly on 2005-07-20
I had a problem with the sound as well at first install and the guide didnt help me either. I went into the BIOS and turned off onboard sound and now my PCI sound card works fine.


On a seperate note, the sound card cost $9.95 a the local computer shop and puts out much better sound than the onboard sound chip did. Its a C-Media 8738.

---

