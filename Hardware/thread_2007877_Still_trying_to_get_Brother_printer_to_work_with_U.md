---
title: "Still trying to get Brother printer to work with Ubuntu"
date: 2012-06-21
forum: Hardware
---

### Post by pottzie on 2012-06-21
I've been trying to get a Brother Hl 2040 printer working with Ubuntu 12.04 for several months, without success. I followed the suggestion from here:[http://ubuntuforums.org/showthread.php?t=1459926](http://ubuntuforums.org/showthread.php?t=1459926)  That I followed:
1. download the LPR driver ([http://welcome.solutions.brother.com...nload_prn.html](http://welcome.solutions.brother.com...nload_prn.html))
2. Open terminal
3. Navigate terminal to location of LPR driver that you downloaded in step 1
4. In terminal, type: sudo dpkg -i --force-all brmfc7340lpr-2.0.2-1.i386.deb
(YOUR FILE NAME MAY DIFFER IF YOUR MODEL IS DIFFERENT)
5. In terminal, type: sudo dpkg -i --force-all cupswrapperMFC7340-2.0.2-1.i386.deb
(AGAIN, FILE NAME MAY DIFFER)
6. Make sure it's installed. In terminal type: dpkg -l | grep Brother

 I used the programs that I downloaded from Brother that were for the printer I'm using, instead of the file that was shown in the post. I can run dpkg -l | grep Brother and bash shows that it's installed, but from there, nothing works.

 I came across another post:[http://ubuntuforums.org/showthread.php?t=1998284&highlight=brother+2040+printer](http://ubuntuforums.org/showthread.php?t=1998284&highlight=brother+2040+printer)

  saying that I needed to ad # Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

 before thet line that reads "# The following rule will disable ..." in /lib/udev/rules.d/40-libsane.rules

 I've added that line to /lib/udev/rules.d/40-libsane.rules, but still don't seem to have a working printer. The added line was from someone trying to get a different model Brother printer working, but I hoped that the manufacturer's info would be the same. Maybe that's where  a problem is, and I don't know it.

 The printer worked before upgrading to Ubuntu 11.04.

---

### Post by kurt18947 on 2012-06-21
Perhaps this will be some help in installing your printer

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

You just download the script into an account with sudo privileges and type the posted line:


[LIST=1]
[*]Run the tool:
**Command: bash linux-brprinter-installer-1.0.4-1 Brother machine name **
[/LIST]
I don't even type the machine name initially.  Just "sudo bash linux-brprinter-installer-1.0.4-1" and press 'enter'**.  **It will then ask for the machine name, run, then list connection choices.  Works pretty well and works the same on 32 bit or 64 bit machines.  Installing scanners can be more of a PITA partly due to a flaw in the .deb installer package.  This might be relevant for you:


[http://ubuntuforums.org/showthread.php?t=1988296&highlight=brother](http://ubuntuforums.org/showthread.php?t=1988296&highlight=brother)

---

### Post by hybenz on 2012-06-25
also had the same problem before, my Brother Hl 2040 printer worked really fine before i made that upgrade to Ubuntu 11.04, kurt's fix seems to be working.. i thought my problem was just low printer toner level..
[IMG]http://fsa.zedge.net/content/2/9/7/3/1-3364179-2973-t.jpg[/IMG]
[[FONT=Garamond][COLOR=White]brother printer toner[/COLOR][/FONT]]("http://www.inkjetsuperstore.com")

---

### Post by pottzie on 2012-06-26
Kurt, thanks for the reply and I apologize for the delay in trying this out. The printer is at my mother's, and I try and work on it when I'm there.

 When I tried to download the script, it just opened up in another window. I see the instructions say that I can right-click on the "accept" button and tell it to "save-as." When I do that in Ubuntu I can only see "save image as.."  When I went with that and then tried to run it from the Downloads Directory, bash didn't work with it. It downloaded as a .gif file, so there's probably no surprise that it didn't work.

 How do I get the file where I can run it? I did "sudo su" to get bash going, then pointed bash to the Downloads Directory, but the .gif image doesn't make bash a happy camper.

 I'm a little fuzzy on the "download the script into an account with sudo privileges" part.

---

