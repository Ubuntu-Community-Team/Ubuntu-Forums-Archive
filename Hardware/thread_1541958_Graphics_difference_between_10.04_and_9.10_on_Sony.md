---
title: "Graphics difference between 10.04 and 9.10 on Sony laptop."
date: 2010-07-29
forum: Hardware
---

### Post by WanderingAlbatross on 2010-07-29
I have recently convinced my wife to switch to Ubuntu, and had installed 9.10 on her machine.  After working through several bugs I received the option through Synaptic to upgrade to 10.04.  Since I couldn't get the liveCD of it to work, I thought this would be a feasible alternative.  Then I would modify Xorg.conf as needed.  For some reason it has been a monster!  I would just like to know what is the big difference between 10.04 and 9.10 on the Xorg.  Why does 9.10 recognize the Intel 82852/82855 so much easier than 10.04?

---

### Post by WanderingAlbatross on 2010-07-30
Okay.  I have narrowed it down to the graphics card.  It is an Intel 855GM.  This card has a long history, and a wonderful amount of effort to improve the situation.  I used workaround A at: [URL="https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes"]https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes

[/URL]Thanks to all who made it possible.

---

### Post by WanderingAlbatross on 2010-08-06
Here is an update:
Issue was not quite fixed with Workaround A.  The computer, a Sony Vaio PCG-TR5AP, would still lock up on graphical work, such as watching YouTube videos.  I tried Workaround B which caused the computer to boot into failsafe graphics mode.  Then I skipped down to Workaround F because that seemed to describe her video card very well.  It seems to have worked, except that Acrobat Player got an error that I didn't notice until after closing the browser.

There seems to be a lot of controversy out there over this graphics issue with this card.  I found some information that basically said that newer kernels are processing some of the graphics that the card themselves use to do.  This speeds up the graphics a bit.  These Intel cards do not like that very much.  Many felt abandoned because their computer seemed abandoned.  I just want to say that I was impressed with the write-ups.  They were very thorough, and gave a lot of options.  Sometimes in the sake of progress, some roads that were being traveled must be left behind, and even abandoned.  I am glad they still reached out and helped those that were on that road.

In windows the usual answer is "You need to buy a new _______."  For those that contributed toward the fix - Thanks!  You are awesome!

---

### Post by WanderingAlbatross on 2010-08-14
Another update:
I ultimately found the above solutions didn't quite work.  

I found this post most helpful:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

This post added a few extra lines to the xorg.conf file:
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "true"   I put mine at "Tiling" "false"

Also it introduced a script to be run at startup.
I was able to get to Safe with it, but Optimal suggestions didn't work, particularly:

$ wget -c [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/linux-headers-2.6.30-02063009-generic_2.6.30-02063009_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.9/linux-headers-2.6.30-02063009-generic_2.6.30-02063009_i386.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/linux-headers-2.6.30-02063009_2.6.30-02063009_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.9/linux-headers-2.6.30-02063009_2.6.30-02063009_all.deb") [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/linux-image-2.6.30-02063009-generic_2.6.30-02063009_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.9/linux-image-2.6.30-02063009-generic_2.6.30-02063009_i386.deb")
$ sudo dpkg -i linux-headers-2.6.30-02063009-generic_2.6.30-02063009_i386.deb linux-headers-2.6.30-02063009_2.6.30-02063009_all.deb linux-image-2.6.30-02063009-generic_2.6.30-02063009_i386.deb

These ended up with an Error File not Found message from the server.  Of course I realize that post was for Jaunty.  Still, is there a way to update to Optimal in Lucid?  It seems some were expecting this problem to go away, but it definitely has not.

The system seems to be doing fine now.

---

