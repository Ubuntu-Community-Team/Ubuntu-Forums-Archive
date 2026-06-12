---
title: "ThinkPad 600E and D-Link DWL-G630 PCMCIA wireless"
date: 2005-08-07
forum: Hardware &amp; Laptops
---

### Post by tonyw50 on 2005-08-07
When I replaced my OS with Ubuntu 4.10 on my IBM ThinkPad 600E at the beginning of the year, my SMC PCMCIA wireless B worked fine and no tweaking was needed.  The same was true when I upgrded to Ubuntu 5.04.  I'd like to start using a wireless G card and have access to a D-Link DWL-630 which I thought I read somewhere would work with the 600E.  Network settings does not recognize it.  What do I need to do to get it to work?  I'm still a Linux novice so will need explicit directions.  Or, is there another brand of wireless G PCMCIA card that would "plug and play" on the 600E?  Thanks for any help anyone can provide.

---

### Post by majnun on 2005-08-08
there is a law in the GNU world : don't ask before digging a while for answers  [-X  :) or you'll be ignored ...

another rule: if you don't provide enough information, nobody is gonna help. \\:D/ 

some thing I'll do if I were you (I'm a newbie too)  .....

- I'll check out that PCI ID is the same for your card than expected (see second link) sometimes they change the chipset ....

- check out the kernel version , use the 2.6 series and latest revision as possible (more support for new cards)
- give the output of dmesg
- give the output of iwconfig
-  search at synaptic for wireless (name and description) utilities
- and of course , spent a time at google searchin for the name of your card followed by linux, debian, ubuntu, problems and all the keywords you think could be useful ....


in short, the process would be : 

 1 - have a kernel with proper wireless support
 2 - have a driver properly compiled and sometime with its proper firmware
 3 - load the firmware + driver
 4 - configure your new device

 
good news :

[http://www.dudek.org/dudek.org/wireless](http://www.dudek.org/dudek.org/wireless)

a place to start :

[http://madwifi.sourceforge.net/dokuwiki/doku.php?id=compatibility_list#dwl-g630](http://madwifi.sourceforge.net/dokuwiki/doku.php?id=compatibility_list#dwl-g630)

good luck ;-)

---

### Post by tonyw50 on 2005-08-09
majnun, 
Thank you for your thoughtful reply.  I did spend numerous hours searching the Ubuntu forums and googling but didn't find anything that I recognized as addressing my problem other than something that said (as your first link confirms) the DWL-G630 card works in Linux.  

The operate word above is recognize - I'm not a techie and I probably came across relevant stuff that I had no c;lue about. 

I really did think that I provided as much information as I knew how to.  For instance, I thought that citing the Ubuntu version and the fact that an SMC wireless card works would indicate that the wireless utility was not an issue.  Following your suggestions, Synaptic shows that the Linux kernel is version 2.6.10 on 386 and that "wireless-tools 27-1ubuntu1" is installed.  Looking at the DWL-G630 card I see a "C2" in the part # BWLG630NA.C2.

I don't know how to get "the output of dmesg" or "the output of iwconfig". When I looked for a driver, I could only find for Windows.  I don't know how to compile anything.  Does all this mean I really must become a lot more technically proficient to use Ubuntu?  I thought Ubuntu was for us dummies.  If the GNU world is only for techies I guess I'll have to reconsider my flirtation with Linux.  I really was enjoying Ubuntu which, once my techie nephew configured it to work with APM on my 600E, works wonderfully with the SMC card.  Sound doesn't work but right now I'm not missing it.

While I appreciate all your efforts at helping me, I really am no closer to figuring out how to get the DWL-G630 card working.  Thanks so much for trying.

---

### Post by firecat53 on 2005-08-12
I've got the DWL-G630 working on an older Dell Inspiron 7000 laptop.

I had to download the source for the madwifi drivers (used for the Atheros chipset which your rev C2 card has) and compile. There are a couple of tutorials and threads that cover this. One is [here](http://ubuntuforums.org/showthread.php?t=38972&highlight=madwifi).
Also check the madwifi page for help in their wiki. 

Scott

---

### Post by tonyw50 on 2005-08-15
Thanks, Scott, for taking the time to respond.  I'll try what you suggest probably this coming weekend.

---

