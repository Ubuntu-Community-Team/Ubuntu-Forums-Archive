---
title: "Grub Error 15/Other Error"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by Greek on 2009-02-16
Hi everyone.
this is my first post
im new to the forums as well as new to Ubuntu
i've been having an issue with Ubuntu, so here goes.
I downloaded the Ubuntu CD and burned it to a disc.
then i restarted my pc (with the Cd in), and used the live preview  (or w.e its called) to look at ubuntu. i liked it, so i installed it with about 50 GB of space. Then i restarted and it showed error 15. So i went on the preview CD again, used the partitioner to delete the partition the ubuntu that didn't work was taking up, then i proceeded with re-installing it and giving it 60 GB of space. and now when i boot my computer it has these options.
( i barely remember the options)
[blah blah = i don't remember]
kernel;optiartic blah blah
kernel blah blah x86 blah
blah blah 
Other Operating Systems
Windows/Longhorn 
Windows/Longhorn

(Note: the two windows longhorn ARE NOT A TYPO, it showed two of the same operating system when i boot my PC)
When i click the first Windows, it shows Choose operating system
Windows Vista
or Ubuntu
when i choose the other, it shows
Windows Vista
or 
Mac Os X (doesn't work, i dont know how to delete this.)

When i do the first option for the kernel of ubuntu, it shows error 15- file not found
when i do the 2nd and 3rd, it shows the same thing.
when i put it the CD and try to go on the live/preview account, it shows a bunch of numbers and errors and it says something like
Error { SDSY }
{HDD} 
[crapload of numbers]
4123058203 kernel:;
-------------
Anyways, i've tried googling a solution and in almost all the places i've looked it has said change something like hdd(0,0) to hdd(1,0), but in my boot options for ubuntu it doesn't say that.
It only says that when i go into options for Windows Vista and it says hdd(0,1) ,so this forum is my last option! I hope you guys help me =]

Some other stuff that might help you guys help me:

Im using vista x32
i have a gateways FX7020 with a 500 GB Hard drive (dont know if sata or w/e)

--
Also, if you guys know how to delete the MAC Os X option in my boot menu, it would be greatly appreciated =]


thanks, and i hope you guys help me

p.s.    hello to all the ubuntu-forumers

):P

**[COLOR="Red"]EDIT[/COLOR]**

not sure if this info. will help, but i'll just post in here incase it has to do something with my problem. [NOTE: i will be filling in the so-called "blah-blah" information later, so you guys can better understand what im saying. (lol)

System Specs: 
[COLOR="MediumTurquoise"]Processor: [/COLOR]AMD Phenom 9600 Quad-Core Processor 2.30 GHz  
[COLOR="MediumTurquoise"]Memory (RAM)[/COLOR] 3.00 GB


[COLOR="Red"][B][U]
EDIT[/U][/B][/COLOR]

[COLOR="Lime"]I CAN NOW BOOT THE LIVECD, AFTER USING WINDOWS VISTA PARTITIONER TO DELETE G: WHICH UBUNTU WAS INSTALLED ON.[/COLOR]
I'm on the LIVECD AS i type this.

---

### Post by caljohnsmith on 2009-02-16
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problems might be.

---

### Post by Greek on 2009-02-16
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problems might be.

Thanks for replying so quickly, but whenever i put my LIVE Cd in it show a bunch of errors with numbers and says something like
{ HDD } { SDSSY } and a bunch of other words and numbers/errors.

UNLESS you mean

burn that file onto my LiveCD Somehow and then it will fix it and then i can use the ubuntu desktop?
sorry im a noob at ubuntu and all this number/command mumbo jumbo
=/

---

### Post by caljohnsmith on 2009-02-16
I thought you could boot your Ubuntu Live CD, because you said originally:
[QUOTE=Greek]I downloaded the Ubuntu CD and burned it to a disc.
then i restarted my pc (with the Cd in), and used the live preview (or w.e its called) to look at ubuntu. [/QUOTE]
So can you still boot the Ubuntu CD? If you can, please download that script to the Ubuntu Live CD desktop and go from there.

---

### Post by Greek on 2009-02-16
> **caljohnsmith said:**
> I thought you could boot your Ubuntu Live CD, because you said originally:

So can you still boot the Ubuntu CD? If you can, please download that script to the Ubuntu Live CD desktop and go from there.

oh, my bad.
i forgot to mention [?] that i cant boot the live CD
it works, but whenever i choose Use ubuntu without changing anything on your computer, it shows that error (previously stated)

---

### Post by Greek on 2009-02-17
Bump
Sorry for the double-post but it would be appreciated if somebody helped me with my problem! The sooner the better =]
Whoever helps me gets
10000 internets
and some orville redenbacher popcorn 
mmmm buttery popcorn
   _________
[[[:popcorn:]]]
   ---------

its locked in that cage and the key is for you to help me
;)

---

