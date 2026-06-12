---
title: "out of frequency i cant take it anymore"
date: 2008-11-02
forum: General Help
---

### Post by kostaz8 on 2008-11-02
i have this annoying problem with ubuntu 8.10 when the ubuntu screen loads my monitor displays "out of frequency" i tryied to configure the x server but nothing and some other things i read from this forum but i couldn't find a solution can someone help me?

---

### Post by Peter09 on 2008-11-02
Install startupmanager, it lets you set your startup screen resolution and refresh rate.

---

### Post by kostaz8 on 2008-11-02
i cant start my pc or connect to the net after the loading screen the only thing i can see is the "out of frequency" message.

---

### Post by laney_1 on 2008-11-02
i had that problem but the screen adjusts itself after about a minute it should continue.

but it is annoying.

laney_1

---

### Post by Peter09 on 2008-11-02
Ahh - didn't realize that. Can you start in recovery mode? Hit escape at the grub prompt and select the recovery option. You will be given a choice to reconfigure your Xserver or drop into command prompt.

Try reconfigure x server first. If that does not work drop into command prompt and type ```
startx
```.

---

### Post by bscbrit on 2008-11-02
Kostaz8, at what point do you lose the screen? Presumably, you can see it during the normal BIOS startup, and I would expect you also to see the Grub menu display (Press 'Esc' during the Grub countdown).

If you lose the screen display immediately after selecting an option from the Grub menu, then we need to use a live disk to edit Grub.  If the screen is OK until after you get to the log in manager, then I suspect we will have to edit xorg.conf.  

Let me know which it is - or what exactly the problem is if it is different!

---

### Post by kostaz8 on 2008-11-02
yes guyz i can go to the recovery mode i tried to fix the xserver but nothing

---

### Post by bscbrit on 2008-11-02
Peter09 replied while I was still typing.  Go with his advice.

Of course, under 8.10 you will find that dpkg-reconfigure xserver-xorg is of little use, as many others including myself have recently discovered.  There is a cure, but it is 'down and dirty' - so I won't go into details yet unless you need it.

---

### Post by Peter09 on 2008-11-02
What happened when you drop into command prompt and typed startx?

---

### Post by bscbrit on 2008-11-02
OK, if you cannot edit the xorg.conf file manually - either through lack of knowledge or can't find a way of doing it, then refer to this post.  But be warned - I TAKE NO RESPONSIBILITY!

[http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

It worked a charm for me :-)

---

### Post by kostaz8 on 2008-11-02
but i cant connect to the internet

---

### Post by bscbrit on 2008-11-02
The two problems are unrelated.  Can you not connect to the internet while in recovery mode?  Do you know how to?

---

### Post by kostaz8 on 2008-11-02
when i hit esc and go to recovery mode i can see that [IMG]http://i434.photobucket.com/albums/qq64/kostaz9/P1010075.jpg[/IMG]
when i hit resume i can see only that [IMG]http://i434.photobucket.com/albums/qq64/kostaz9/P1010076.jpg[/IMG]
 "&#931;&#919;&#924;&#913; &#917;&#922;&#932;&#927;&#931; &#927;&#929;&#921;&#937;&#925;" means "out of frequency"

---

### Post by bscbrit on 2008-11-02
Try the bottom option ' -Try to fix X server'.

Once that is finished, it will return to this menu.  At that point, try to 'Resume normal boot' and see if that gets you back to a usable screen.  If not, come back and let us know what has happened.

---

### Post by kostaz8 on 2008-11-02
nothing happened like i never fixed the xserver

---

### Post by Peter09 on 2008-11-02
can you drop to root shell prompt and type startx?

---

### Post by kostaz8 on 2008-11-02
it does the same :(

---

### Post by bscbrit on 2008-11-02
I'm a bit confused. You are chatting with us on this forum but you claim that you cannot download from the internet.  How are you using this forum?

---

### Post by kostaz8 on 2008-11-02
im using my other pc .
I dont think that we can find a solution should i reinstall linux to get over with?

---

### Post by bscbrit on 2008-11-02
Well, that is entirely up to you.

But, before you do, how did you upgrade last time?  Did you install from a live disk or did you upgrade using Upgrade Manager?  If it was a live disk, did you burn it yourself?  If you did, check it against your downloaded file to make sure that there are no corruptions on the disk.  I would always recommend burning it at a much slower speed that either the disk or the burner claim they can cope with.  For example, I will burn at 10x although the CDs claim to be x52 - much slower but I don't get any burn errors.  The extra time taken - perhaps a minute or two - I go and have a coffee.  Life is not that short that everything must be done at the fastest possible speeds.

Secondly, before you do, try the following in a terminal:

sudo lshw >lshw.txt

That will produce a text file (lshw.txt) that contains all the hardware in your system that Ubuntu has recognised.  Check it to make sure it is what you expected.  If you want to, attach it to your next reply here so we can see what hardware you have and we can try to identify solutions for potential problems.

Alternatively, just try to re-install if you have no data worth keeping on your hard drive.

Good Luck!

---

### Post by bscbrit on 2008-11-02
If you have a live disk, try booting from that disk.

Assuming that it works, copy the file /etc/X11/xorg.conf to a thumb drive.  Reboot into your installed version, copy the file over the installed xorg.conf and you should have a working screen.

---

### Post by kostaz8 on 2008-11-02
i had been using ubuntu for a moth then i read about the new upgrade ubuntu 8.10 in a part of the upgrade i was asked if i want to reinstall all my software i didn't know what will happen and i clicked do reinstall it then i restarted my pc after that i couln't start my pc because i had a problem with the xserver. Tried everything i could to repair but i coulnt, so i downloaded ubuntu 8.10 from my other pc after that i burned it to a cd and started the re installation the cd had a problem and i got an error "I/O Read Error" something like that.I checked the download it was 699mb and the file i had was 698 lol! i downloaded it again burned it in slow speed reinstalled again and then appeared the problem with my screen.

sudo lshw >lshw.txt gives me something this 

CPUID

PCI (sysfs)

---

### Post by kostaz8 on 2008-11-02
> **bscbrit said:**
> If you have a live disk, try booting from that disk.

Assuming that it works, copy the file /etc/X11/xorg.conf to a thumb drive.  Reboot into your installed version, copy the file over the installed xorg.conf and you should have a working screen.

tried to boot from cd but the SAME Oh MY GOD!

---

### Post by bscbrit on 2008-11-02
LOL - that's what you saw on the screen!

Have a look in the file lshw.txt - it should be several pages long! Try this in a terminal window -

cat lshw.txt | less

cat - will display the file (lshw.txt)
| - will 'pipe' the output (i.e. send the text) to the 'less' program.
less - will let you page through the file from the command line.

I hope there is more than what you saw on the screen.

---

### Post by bscbrit on 2008-11-02
"tried to boot from cd but the SAME Oh MY GOD!"

I suspect that the CD is bad.  Try burning another one at S L O W speed.  And please attach the file lshw.txt to your next reply so that I can look at what hardware you have.

---

### Post by kostaz8 on 2008-11-02
says cat: lshw.txt: no such file or derectory
          (END)




maybe if i could somehow change the resolution or something?

---

### Post by bscbrit on 2008-11-02
OK, then do this

sudo lswh | less

that way it will not make a file but you will be able to check the hardware that Ubuntu has found.

---

### Post by kostaz8 on 2008-11-02
again the same 

sudoL lswh L command not found

forget it i quit i'll reinstall it 
thnx for your help

---

### Post by bscbrit on 2008-11-02
Ah, that's what you're typing wrong.

The pipe symbol is '|' but that is not a letter l.  On an English keyboard it is the character left of and next to the 'z' which is on the same key as the '\'. It might appear on the keyboard as two vertical lines with a slight gap between them, but it prints as a solid vertical line.

People often criticise the use of the command line but, as you have discovered, when software doesn't do what you expect then it is the only way you can interact with the computer.  It is always a skill worth having even if you do not intend to use it very often.

If your re-installation does not work the second time, then I would suggest that you re-install 8.04 and then we can move forward from there.  Once you have a working system it is a lot easier to upgrade because we can copy the working display files from 8.04 to 8.10.  They will still work on Intrepid.  Secondly, we can also save your working internet/network connection files so that we can ensure that your new system also connects easily.

Good Luck with the re-installation!

---

### Post by kostaz8 on 2008-11-03
At last i uninstalled ubuntu and make 3 partitions for windows ubuntu and 1 for my data.Now i don't know how to configure the 3rd partition and win and can read it.

---

### Post by bscbrit on 2008-11-03
Hi Kostaz8!  The partition types that both Windows and Ubuntu can read and write easily are FAT32 and ntfs.  Writing to ntfs still has a small risk associated to it (but I have not experienced any problems in over a year of doing so) so you might prefer to format your shared partition as FAT32.

You will need at least 2 partitions for Ubuntu, a main partition and a swap partition of say 512MB.

---

