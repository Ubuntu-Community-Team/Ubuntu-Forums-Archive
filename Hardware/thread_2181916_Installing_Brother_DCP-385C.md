---
title: "Installing Brother DCP-385C"
date: 2013-10-19
forum: Hardware
---

### Post by Richard_York on 2013-10-19
I've just jettisoned Windows, and am now on Ubunti 12.04, as of 3 hours ago! Phew.
I can't get my Brother DCP-385C printer-scanner to install. 
Tried the "Printer" tag on the systems menu, and it refuses to find a driver, other than "generic" which doesn't seem to work at all. 
Tried advice at[ http://ubuntuforums.org/showthread.php?t=590793]("http://ubuntuforums.org/showthread.php?t=590793") which dates from 2007. This pointed me to [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)  where I downloaded the .deb options for both LPR and cupswrapper. (I haven't a clue what these either LPR or cupswrapper means, and hope I don't need to :)   )
The first installed OK, according to the console. The second, after several attempts both to re-install and with re-downloading, insisted there's an error in it.
I also tried downloading it & going through the Ubuntu Software Centre icon on the desktop, where it recoginsed them as being there, but advised me these downloads had errors & didn't want to install them.

So I'll really welcome advice on how to get my printer/scanner working. My wife & I both use this computer for work, so we're stuffed without it.

Thanks.

---

### Post by slipjig on 2013-10-21
Hi Richard,

I think I managed to get those drivers installed, although as I've not got your printer/scanner, I can't verify.  I'm using 12.04 too, and here's what I've done:

Downloaded the two same two files from Brother which you did:
dcp385clpr-1.1.2-2.i386.deb and dcp385ccupswrapper-1.1.2-2.i386.deb

I downloaded these both into a folder called tmp in my home directory.  So /home/mark/tmp

I opened a terminal, and typed:

> cd tmp

To check you're in the right place, you can also run (by which I mean type [command] and hit <enter>:

> pwd

and

> ls

which first tells me I'm in /home/mark/tmp/ and then lists all the files in that location, where I see the two I've just downloaded.

So, preamble over, I then ran this (from the instructions you followed):

> sudo mkdir /var/spool/lpd

Next I ran the following (here you can see both my commands (in bold), and the output the terminal gave me back to confirm things - with "$" representing the empty/ready prompt:

> $ **sudo dpkg -i dcp385clpr-1.1.2-2.i386.deb**
Selecting previously unselected package dcp385clpr.
(Reading database ... 439959 files and directories currently installed.)
Unpacking dcp385clpr (from dcp385clpr-1.1.2-2.i386.deb) ...
Setting up dcp385clpr (1.1.2-2) ...
$

That went swimmingly well, apparently.  So next I ran:

> $ **sudo dpkg -i dcp385ccupswrapper-1.1.2-2.i386.deb**
Selecting previously unselected package dcp385ccupswrapper.
(Reading database ... 439981 files and directories currently installed.)
Unpacking dcp385ccupswrapper (from dcp385ccupswrapper-1.1.2-2.i386.deb) ...
Setting up dcp385ccupswrapper (1.1.2-2) ...
cups stop/waiting
cups start/running, process 9815

So, that tells me the package installed without error.  However, I didn't get the terminal back.  If all was perfect, I would expect to get my dollar sign back.

We can interupt programmes running in a terminal with CTRL+C.  When I typed that, I got the following (The "^C" represents me hitting CTRL+C):

> ^Cdpkg: error processing dcp385ccupswrapper (--install):
 subprocess installed post-installation script was interrupted
Errors were encountered while processing:
 dcp385ccupswrapper
$

So although this reports errors, it does look like the package has installed to me.  If I open up Synaptic Package Manager (you might not have this installed yet, but the "Software Center" does a similar thing), and I searched "brother", I can see the packages installed normally:

[IMG]http://flet.org/links/screen.png[/IMG]

I can't go any further than this, because I don't have the device to test.  But it does nominally look like I've installed the drivers OK.  The error I got could be because the driver installer is just a bit out of date with the way Ubuntu works today.  From here, I'd expect to be able to do the rest through the normal printer settings - i.e. no more terminal (yay!).

Don't know if this helps?

---

### Post by Richard_York on 2013-10-21
Wow, that's superb, thanks Mark. I'll do that and report.

---

### Post by slipjig on 2013-10-21
I would recommend installing Synaptic Package Manager, if you've not got it already.  It's the best non-terminal way of determining exactly what's on your system and installing/removing things.  Quicker and more focused than "Software Center"; and for this specific problem, it would help you determine if any of your attempts have already installed one or both of the packages, and help you remove them and try again if you need to.

Installing Synaptic can be done from the Software Center, or in a terminal with "sudo apt-get install synaptic".

---

### Post by Richard_York on 2013-10-21
I did that, as part of the process. Very useful.
 It showed me green tabs on Brother components, as does your screen shot above, but with different numbers on to the ones your screen shot showed, so I took the risk of telling it to get rid of them to make way for the new installations. Dunno if that was the right thing to do, but it seems to have worked so far. :-)

Still haven't got to seriously looking for how to scan...

---

### Post by slipjig on 2013-10-21
There are similar scanner drivers listed here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

Try them and see. Looking at that link, I'd assume you'd need "brscan3 32bit" and "scan-key-tool 32bit".

The command to prepend to each file name would be "sudo dpkg -i".

"sudo", means "run this command as root". "dpkg" is the very low-level (i.e. does only simple stuff) "Debian Package tool", and the "-i" option tells it to run in "install mode". So:

> $ sudo dpkg -i [filename]

- always making sure you "cd" into the folder these files are in first.  If you're new to the terminal, this page: [http://linuxcommand.org/lc3_lts0010.php](http://linuxcommand.org/lc3_lts0010.php) and the following chapter will help you make better sense of what you're doing here.  Try not to enjoy it too much, or you might find yourself using the terminal more and more ;P

Using dpkg can't go badly wrong, as it will only ever install that file and nothing else. If the file won't work on your system, the Debian Package system is clever and protects you from messing up your software configuration. So, it'll either work (and your packages will be installed, or it'll fail with a (hopefully useful) error message and nothing done/changed on your system.

---

### Post by Richard_York on 2013-10-21
You're ahead of me! I'll try that, though first food is needed... more later!

---

### Post by Richard_York on 2013-10-21
I tried that.
 Well, I accidentally tried the lazy way first - I must have double-clicked on the package while moving it to tmp, and the Ubuntu Software Centre opened up and offered to install it for me. So I asked it to carry on. It announced there was an error, but offered to install anyway, so I went ahead. It didn't make the scanner work, so I tried again via the terminal.
I get "dpkg: error: dpkg status database is locked by another process"
So I wondered if I'd spoilt it by trying it with the lazy way, removed that file, downloaded another, and still get the same dead end, whether I try the driver or the skan key package.
Dunno how to get round this yet.

---

### Post by slipjig on 2013-10-21
Just tried the scanner drivers.  They installed smoothly without issues, and didn't need any additional directories creating.

So, download the following files from: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3)

brscan3-0.2.11-4.i386.deb (brscan3 32bit)
brscan-skey-0.2.4-1.i386.deb (scan-key-tool 32bit)

This time, there's no need to create an additional directory as we did with the printer.  It was an unusual step before, and probably only necessary because the package hasn't been updated alongside changes to Ubuntu.  So we're shoehorning historical packages into place here.  I found the creating of a new directory necessary with the printer drivers, because dpkg complained about that directory not being present.  But the scanner drivers went on without any complaint.

Once you've got the files, you can install them the terminal way exactly as for the printer drivers, but with the new file names instead:

> mark@yupa /home/mark/tmp $ **sudo dpkg -i brscan3-0.2.11-4.i386.deb**
[sudo] password for mark: 
Selecting previously unselected package brscan3.
(Reading database ... 439959 files and directories currently installed.)
Unpacking brscan3 (from brscan3-0.2.11-4.i386.deb) ...
Setting up brscan3 (0.2.11-4) ...

mark@yupa /home/mark/tmp $ **sudo dpkg -i brscan-skey-0.2.4-1.i386.deb**
Selecting previously unselected package brscan-skey.
(Reading database ... 439979 files and directories currently installed.)
Unpacking brscan-skey (from brscan-skey-0.2.4-1.i386.deb) ...
Setting up brscan-skey (0.2.4-1) ...

mark@yupa /home/mark/tmp $

Or, if you want to experience something different, you can open your file browser, navigate to the files you've downloaded, and just double-click on them.  This will open them with Software Center.  Allow a short pause when Software Center opens before it displays the file you want to install, and then just click the "Install" button and put in your password to confirm.  The brscan3 package raised a complaint about it being a bad quality package.  I clicked the option "Ignore and install anyway" and the install completed without further problems.

I checked this process out for you because I was curious.  I've never installed a .deb file this way before.  Prettier, but slower and more confusing to my tastes, but each to their own!  You have a choice of install methods now.  Enjoy :)

---

### Post by slipjig on 2013-10-21
Oops!  Our posts collided, and you found the lazy way "by accident".  Good for you :)

The error you get is because only one program can use dpkg at a time.  Installing from the command line is doing exactly the same thing as installing by the Software Center.  But if the Software Center is open, dpkg from the command line will complain in exactly the way you've seen.

If you've installed both packages and the scanner still doesn't work, then I'm not the best person to help you further.  I'd try restarting the computer after installing the packages, in case the drivers are normally enabled at boot.  But I'm not sure beyond that, as I haven't used a scanner for years.

---

### Post by Richard_York on 2013-10-21
erm, cough, blush, I'm getting tired. I hadn't actually noticed the skan-key (Skanky???) first time round. So I'm trying again. Will report back.

---

### Post by slipjig on 2013-10-21
There's also general scanner advice here: [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

### Post by Richard_York on 2013-10-21
Done that, thank you, and all went well, except.... that it's not working, still !
"Simple Scan" fails to find a scanner, and scanning by pressing the button on the machine results in it failing to connect to the computer.

if you get time, what if anything shows in your synaptic package manager window as being installed, please?
I also looked at [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)
where it wants me to edit things. 

Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04, 12.10
**1.** Open "/lib/udev/rules.d/40-libsane.rules" file.
**2. **Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"".    
  
  The lines to be added---------------------------   
       
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
      **3.** Restart the OS.


This chimes with some comments I've seen on other threads on the matter, but I'm still worried about turning my terminal into a terminator, I think!

I haven't yet pursued the link to the Terminal instructions you gave to any depth yet, so still not at all sure how to actually follow these instructions. Simply opening Terminal and copying in part of the first line in quotes results in this:

richard@richard-GA-MA790X-UD4:~/tmp$ /lib/udev/rules.d/40-libsane.rules
bash: /lib/udev/rules.d/40-libsane.rules: Permission denied
richard@richard-GA-MA790X-UD4:~/tmp$ 

At least I vaguely know now, from your link, what a bash is, but dunno what to do with it.

Sorry!

---

### Post by slipjig on 2013-10-22
**Bad news first**

I've done a bit more trawling, and while I suspect it's most likely possible to get your scanner working, it seems Brother scanners have caused a lot of people a lot of headaches installing them in 12.04 and on.  It's your choice to continue if you like a challenge, but you might also decide it's easier to get another scanner for the time being.  I just thought it was worth saying that up front.  I personally get by with this stuff by looking for the low hanging fruit.  Your scanner is right up there on a tricky branch, I fear.

**Verifying that the brscan packages have installed:**

Open Synaptic and search for "brscan".  If the packages are installed, you'll see brscan3 and brscan-skey highlighted green as installed.

**Editing system files**

You've been asked to edit files outside your home directory.  It's a shame you've hit this so soon in your Ubuntu experience - it's not often needed.  But it's not very hard once you get a bit familiar with it.  The main problem you've got to get around is that you're not allowed to edit files outside your home directory.

First off, know that software on Linux is configured almost entirely through text files.  These are easy to work with in a text editor.  Ubuntu provides a text editor called, strangely, Text Editor (although its real name is "Gedit").  This is similar to Notepad on Windows, but better, obviously ;)

You could open Text Editor (aka Gedit) through your menu, then do File > Open, then browse "File System" (in the shortcuts menu on the left) for the file you need to edit.  However, that would open the file as you, and you're not allowed to change it.  So to open and edit system files, it is better to do it through the command line.  For the example you've been given, you'd do:

$ sudo gedit /lib/udev/rules.d/40-libsane.rules &

The ampersand on the end is optional, but opens gedit in such a way that your terminal is freed up for other things (marginal benefit for what you're doing). Without the ampersand, your terminal will not respond to anything until you close gedit - and if you close the terminal, gedit will evaporate too.

However - **important footnote** - when I tried to edit /lib/udev/rules.d/40-libsane.rules to test this, I found that it wasn't there.  So I suspect the file you need to edit has moved somewhere else, and the instructions you were following are out of date.  How we find the location of that file, I don't know.  Someone else might help us, or you might find the answer by Googling for hours.  Personally, I'd be off down to the nearest retail outlet that sells cheap scanners ;)

---

### Post by Richard_York on 2013-10-22
As ever, more superstar spandex points, and thanks for your patient thoroughness!
I will try this.
Today's more pressing issue meanwhile ... NOT one I expect you to solve!  ... is that Libreoffice, which was doing mailmerge nicely on my letters & invoices to schools & things, has now decided to cease talking to my data source, so at present I have to laboriously copy all the details into each one by hand. 
This is more urgent, as I now have a pile of work admin to catch up on, having spent the last three days on installing the rest and bothering you for advice! Again, this is not a problem I expect you to address! Then I'm off on work travels this afternoon.
When I get to try your latest, I'll report back.
And then I'll probably just go & buy a scanner!
Meanwhile I've just gleefully printed out Google maps to find where I'm going :)

More anon....

---

### Post by Richard_York on 2013-10-23
Greetings! I tried
 sudo gedit /lib/udev/rules.d/40-libsane.rules &
in the terminal.
It didn't ask for my password, just responded with [1] 3314
I have tried looking for a translation of this response, not found any yet. Does this mean my machine hasn't got that file in the expected location either?  Or is it trying to tell me something very profound?
Could indeed be a case of cheap scanner here we come!

(Don't you wish I'd spent longer in Wolverhampton now?! ;)   )

---

### Post by Richard_York on 2013-10-24
OK, I submit! It's going to have to be
"$ sudo scanner buynew geddit hopeitworks"
time.
But we DO have a printer which seems to do as well as it used to, as a printer!
So once again, very many thanks.

---

### Post by khanw on 2013-10-30
Hi Richard,

Thought I post a quick reply, as I've been struggling to get my Brother DCP-385C scanner to work and trying to follow your thread to get as far as possible. And, like you, I failed...initially. Before I continue though: I'm using Ubuntu 13.04, so I don't know to what extent this post will apply to your situation.

I did two things wrong:
1) I accidentally used the brscan2 drivers instead of the brscan3 ones (slight chance of you making the same silly mistake, but you never know :-) )
2) The instructions on the Brother site tell you to use the --force-all option on installation, so 'dpkg -i --force-all brscan3-0.2.11-4.i386.deb'. I had initially forgotten this

It still needed a reboot to make the scanner be recognised, but now 'brscan-skey -l' lists my scanner and simple-scan also works!

As a final remark, I noticed slipjig mentioned that the file /lib/udev/rules.d/40-libsane.rules doesn't exist on 12.04. I found in another post (
[http://ubuntuforums.org/archive/index.php/t-1340908.html]("http://ubuntuforums.org/archive/index.php/t-1340908.html")) the following alternative location for the edits:

 /lib/udev/rules.d/50-udev-default.rules

Maybe this will bring your scanner to life...

Good luck!

---

### Post by Richard_York on 2013-10-30
Thanks for this, Khanw! 
I'm glad your machine now works. You'll be entertained to learn that just yesterday I gave in & ordered a Canon Lide 110 scanner - I think it's their cheapest, and it's now plugged in. With SANE installed it works perfectly, with just pluggin in, as far as I've had time to find out so far.

Perhaps I should try looking at the edit you found, in case it works on my Brother machine, & Curry's could have their Canon back... !!
Meanwhile this information is up there for anyone else fighting the Brother installation.

Thanks again!

---

