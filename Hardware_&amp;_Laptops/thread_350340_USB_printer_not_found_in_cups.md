---
title: "USB printer not found in cups"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by steve.dhondt on 2007-01-31
Hi I'm having some difficulties installing my Lexmark z13 USB-printer.
I got the right ppd-file, but the problem I have is that my printer isn't found. The only options in the droplist I got are: 

-Hp no_device_found
-LPT
-Parallel port #1 (canon)
-Parallel port #1 (Epson)

I know those last three can't be it since it's USB, so the law of elimination tempted me to try the first one, but that obviously didn't work.

Could anyone please run me trough how to set this right? Also, please keep in mind I'm a total noob :D I just installed ubuntu 6.10 a while ago and it's my first linux-expierience. 
Thanks in advance...

---

### Post by loserboy on 2007-01-31
did you check to see if that printer is supported?

edit: I made a quick look at the wiki and only saw the z23 as being supported, but I'm gonna check some other places.

---

### Post by steve.dhondt on 2007-01-31
To be honest I wouldn't know where to check that. Is there a checklist available or did you mean google it?
anyway, the PPD files skipped version Z13 it goes from Z11, Z12 to Z22 But I hoped either Z12 or Z22 should work for it.

---

### Post by loserboy on 2007-01-31
you would think that close numbers would work but I had the same problem with a samsung I had, i guess they change the drivers completely.

anyway you can check the wiki on this site, or you can google something like "ubuntu compatible printers"


this is for the z23

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ23?highlight=%28printers%29](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/LexmarkZ23?highlight=%28printers%29)

---

### Post by jml on 2007-01-31
This link does not refer to your precise Lexmark Printer, but you might be able to use the information to help you get connected.

[http://www.ubuntuforums.org/showthread.php?t=49714&highlight=Lexmark+Printer+installation](http://www.ubuntuforums.org/showthread.php?t=49714&highlight=Lexmark+Printer+installation)

By the way, I found this link by typing in the terms "Lexmark Printer Installation."  in the search box at the top of this page.  It often gives good leads to find an answer to your questions.  Oh, and by the way, welcome to Ubuntu, and to this forum!

Joe

---

### Post by loserboy on 2007-01-31
hey i think i found it, have a look

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z13](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z13)

---

### Post by steve.dhondt on 2007-01-31
Ok I'm trying that last link as I'm writing this. Thanks a lot for the fast replies :)
I expected I'd have to wait at least a couple a days before someone would notice the tread, so that was a nice surprise  :p

---

### Post by steve.dhondt on 2007-01-31
I'm still not in the clear. I got the foomatic kit and got the right driver from the lexmarksite
I did ./install 

```

[root@ /home/steve/lexmark-foomatic-kit]# ./install
./
./opt/
./opt/lexmarkinkjet-Dither.xml
./opt/lexmarkinkjet-Resolution.xml
./opt/lexmarkinkjet-ImageType.xml
./opt/lexmarkinkjet-AlignA.xml
./opt/lexmarkinkjet-AlignB.xml
./opt/lexmarkinkjet-AlignC.xml
./opt/lexmarkinkjet-AlignD.xml
./opt/lexmarkinkjet-AlignE.xml
./opt/lexmarkinkjet-AlignF.xml
./opt/lexmarkinkjet-PageSize.xml
./opt/lexmarkinkjet-Port.xml
./opt/lexmarkinkjet-MediaType.xml
./opt/lexmarkinkjet-InkType.xml
./opt/lexmarkinkjet-Model.xml
./driver/
./driver/lexmarkinkjet.xml
Kit successfully installed! The list of written files you find in /usr/share/foomatic/kitload.log.

root@ /home/steve/lexmark-foomatic-kit]# 
```
the next line in the instruction-file tells me: 
[I]"in a terminal window. In the beginning of the lexmark* files there are
definitions of some paths. Adapt them to your system (under Mandrake
Linux 7.2 or newer you do not need to modify them and on RedHat or
Conectiva probably not, too)."[/I]
But I don't exactly understand what they mean with that. 

When I do lexmarkinstall I get this:
```

[root@ /home/steve/lexmark-foomatic-kit]# lexmarkinstall

Lexmark inkjet printer installation program
-------------------------------------------

(C) 2001 by Till Kamppeter
Free software under the terms of the GNU General Public License (GPL)

To install your Lexmark Z13, Z22, Z23, Z32, Z33, Z52 or Z53 on this system
you need to install the drivers provided by Lexmark at first. Please download
them from the Lexmark home page (http://www.lexmark.com/)
If you have a Z22 use the Z32 driver, these two printers
are the same hardware. The Z23 uses the driver for the Z33. You do not need
to install LPD for installing the Lexmark drivers, just use the printing
system which is already installed. When a window shows up during the
the installation of the Lexmark driver, close it. If you get an error
message in the end of the installation of the Lexmark driver, ignore it.
Start this program again afterwards to configure your print.
```
But I already installed the driver trough cups, I geuss I need to install it again with this kit, but I don't know how.

I also tried changing "dev/lp0" into "dev/usb/lp0" in etc/cups/printers.conf but that still didn't do the trick, and if I look at printer-properties it still hasn't got the right location.

Now I have no idea what still needs to be done.

---

### Post by loserboy on 2007-01-31
hmmm, over my head....

but i think we're close.

---

### Post by steve.dhondt on 2007-02-04
I didn't get much time the last few days to look at this problem, but I did find a few things the other day. First of all, I feel like a complete idiot for not noticing this before, but one of my usb-ports doesn't seem to be working. So by plugging it in a different port at least I got cups to recognize my printer and I got it to install the right ppd file, but it's still not printing.

in the properties menu it says: *Ready: /usr/lib/cups/filter/foomatic-rip failed*
I opened that file to take a look
first two lines said: 
```
#!/usr/bin/perl
# The above Perl path may vary on your system; fix it!!! -*- perl -*-
```
I checked that and perl is indeed located at /usr/bin/
So I simply unquoted that first line. However I don't know why that exclamation mark is doing there, should that be removed to? I tried both with it as without it,  and it still said */usr/lib/cups/filter/foomatic-rip failed* in the printer-properties-menu.

Then it said:
```
# Save it in one of the directories of your $PATH, so that it gets
# found when called from the command line (for spooler-less printing),
# link it to spooler-specific directories when you use CUPS or PPR:

#    ln -s /usr/bin/foomatic-rip /usr/lib/cups/filter/
#    ln -s /usr/bin/foomatic-rip /usr/lib/ppr/lib/
#    ln -s /usr/bin/foomatic-rip /usr/lib/ppr/interfaces/
```
I tried that but apparently that wasn't necessary as the terminal told me: "File exists"

then I tried changing the following lines of taht file:
```
my $spooler = 'direct';
``` into:
```
my $spooler = 'cups';
```
still no change

finally I tried "*chmod 777*" on both the usb and the foomatic-rip, but it still says: /usr/lib/cups/filter/foomatic-rip failed
and refuses to print anything

---

### Post by loserboy on 2007-02-05
> #!/usr/bin/perl # The above Perl path may vary on your system; fix it!!! -*- perl -*-



> I checked that and perl is indeed located at /usr/bin/
So I simply unquoted that first line. However I don't know why that exclamation mark is doing there, should that be removed to? I tried both with it as without it, and it still said /usr/lib/cups/filter/foomatic-rip failed in the printer-properties-menu.



if you are talking about _#!_/usr/bin/perl, that part should be left alone, it tells it to use perl to execute.

but thats all i know, im sorry.

when i get some time i'll look into it more, at least we know it can be done.  have you tried posting at the linuxprinting forum?

---

### Post by steve.dhondt on 2007-02-05
> if you are talking about #!/usr/bin/perl, that part should be left alone, it tells it to use perl to execute.

I thought quoted lines (the ones with a #-symbol in front) didn't do anything, that's why I thought that they meant unquote it when they told me to "fix it"

---

### Post by loserboy on 2007-02-05
normally they do, but as i just learned recently from python, if you add that #!/(path)

its saying that the file is made to be executed by a program and thats the path to it, I think the "fix it" part is just saying make sure the path to perl is right.

---

### Post by loserboy on 2007-02-05
have yo tried doing all the steps from scratch now that you have it plugged into the recognized port?

also 
> 
the next line in the instruction-file tells me:
"in a terminal window. In the beginning of the lexmark* files there are
definitions of some paths. Adapt them to your system (under Mandrake
Linux 7.2 or newer you do not need to modify them and on RedHat or
Conectiva probably not, too)."
But I don't exactly understand what they mean with that. 

can you find those files it's talking about and post them, they prolly just need to be redirected to ubuntus setup


Edit: I went ahead and started a topic in the linuxprinting forums you can see how it turns out [here]("http://forums.freestandards.org/read.php?29,828")

---

### Post by steve.dhondt on 2007-02-06
> **loserboy said:**
> have yo tried doing all the steps from scratch now that you have it plugged into the recognized port?
Yep I did that several times after making modifications.

> can you find those files it's talking about and post them, they prolly just need to be redirected to ubuntus setup
Ah yes, I almost forgot about that. There are three lexmark* files (Lexmarkinstall, lexmarkwrapper and lexmarkmaintain) in the lexmark-foomatic-kit folder. 
all three of them seem to have a list so now I'm thinking they probably put that star in the instructions to refer to all three of them. First I thought the star was there because the names would differ on different systems, silly me :)
anyway, I'll copy them here, but first I think there's something else that's probably more relevant.

Some thing else that might get us closer to the problem. Remember how I said that lexmarkinstall only brought me the following text: 
*"To install your Lexmark Z13, Z22, Z23, Z32, Z33, Z52 or Z53 on this system you need to install the drivers provided by Lexmark at first. Please download them from the Lexmark home page ([http://www.lexmark.com/](http://www.lexmark.com/)) If you have a Z22 use the Z32 driver, these two printers are the same hardware. The Z23 uses the driver for the Z33. You do not need to install LPD for installing the Lexmark drivers, just use the printing system which is already installed. When a window shows up during the the installation of the Lexmark driver, close it. If you get an error message in the end of the installation of the Lexmark driver, ignore it. Start this program again afterwards to configure your print."*
Even though I had already done that trough cups.
Well now that I was looking at the lexmarkinstall file I noticed it said:
 
```
**if (! -d $lexmarkpath) {**
  print "\n";
  print "Lexmark inkjet printer installation program\n";
  print "-------------------------------------------\n";
  print "\n";
  print "(C) 2001 by Till Kamppeter\n";
  print "Free software under the terms of the GNU General Public License (GPL)\n";
  print "\n";

  print "To install your Lexmark Z13, Z22, Z23, Z32, Z33, Z52 or Z53 on this system\n";
  print "you need to install the drivers provided by Lexmark at first. Please download\n";
  print "them from the Lexmark home page (http://www.lexmark.com/)\n";
  print "If you have a Z22 use the Z32 driver,  (and so on...)

```
So that line in bold should probably lead us to the problem. But I don't know what they mean by (! -d $lexmarkpath)

Because of the problems with the usb-port I had forgotten all about this problem with the lexmarkinstall
So it's probably pointless to fix the paths from the lexmark* files before first installing it decently, sorry for the bad information.

Anyway I'll go ahead and post the the lines from the lexmark* files either way, they are:
Lexmarkinstall:
```
#  === ADAPT THIS TO FIT TO YOUR ENVIRONMENT ==========
my $lexmarkpath = '/usr/local/lexmark';
my $nulldevice = '/dev/null';
my $grep = '/bin/grep';
my $cat = '/bin/cat';
my $cut = '/usr/bin/cut';
my $head = '/usr/bin/head';
my $tail = '/usr/bin/tail';
my $wc = '/usr/bin/wc';
my $ls = '/bin/ls';
my $config = '/usr/bin/foomatic-configure';
# =======================================
```

Lexmarkwrapper:
```
# === ADAPT THIS TO FIT TO YOUR ENVIRONMENT ===============================
# The name of the GhostScript executable, add the path if it is not in the
# standard path for executables
my $ghostscript = "gs";
# The path where your Lexmark printer driver is installed
my $lexmarkpath = "/usr/local/lexmark";
# =======================================
```

Lexmarkmaintain:
```
# === ADAPT THIS TO FIT TO YOUR ENVIRONMENT ===============================
my $lexmarkdir = '/usr/local/lexmark/';
my $grep = '/bin/grep';
my $cat = '/bin/cat';
my $cut = '/usr/bin/cut';
my $head = '/usr/bin/head';
my $tail = '/usr/bin/tail';
my $wc = '/usr/bin/wc';
# ================================================
```

> Edit: I went ahead and started a topic in the linuxprinting forums you can see how it turns out [here]("http://forums.freestandards.org/read.php?29,828")
Ok thanks, I bookmarked the link. thanks for all your help so far.

---

### Post by loserboy on 2007-02-06
np, but i don't really feel like i'm helping, im pretty much a noob too.

are you able to actually find those files in the paths stated as in:

is grep in /bin/grep, cat in /bin/cat, etc?

I would think especially important are these lines correct?
my $lexmarkpath = '/usr/local/lexmark';
my $config = '/usr/bin/foomatic-configure';



and on this part 
> if (! -d $lexmarkpath) {
  print "\n";
  print "Lexmark inkjet printer installation program\n";
  print "-------------------------------------------\n";
  print "\n";.......
that just looks like a command saying: IF the conditions are right(something about the lexmark path), then PRINT the next set of lines

---

### Post by steve.dhondt on 2007-02-06
> hat just looks like a command saying: IF the conditions are right(something about the lexmark path), then PRINT the next set of lines

Yeah i thought so, but the thing is, I think when those conditions are met, and he does print them, that he stops the installation and does not continue with the other lines from that install file. That's why I'm thinking that mentioned condition is what's currently wrong, and thus should lead to the problem.

I tried by installing the driver manually instead of trough cups but then I get:

> [root@ /home/steve/lexmark-foomatic-kit]# sh lexmarkz13-1.0-3.sh
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
OK
Uncompressing Lexmark Z13 Printer Drivertrap: 125: cd /tmp; /bin/rm -rf $tmpdir; exit $res: bad trap
So I think that only gets us further away from the problem.

> np, but i don't really feel like i'm helping, im pretty much a noob too.
LOL, don't say that, I would still be several steps behind if you wouldnn't have pointed me in the right direction now and then :)

---

### Post by loserboy on 2007-02-06
ok so you're saying it prints that ona failed condition, it looked like it was saying print on a success condition.


if you already checked those paths and they all were correct, then im really at a dead end here, I did some more googling.......have you thought about a small printer investment? how do you even find ink for that thing?

---

### Post by steve.dhondt on 2007-02-07
Ok, I'll just look a bit further, I feel like I'm already getting close thanks to your help so far. 
And ink is still available in all department-stores :)
Lexmark has universal cartridges for most of it's printers. That way even the older ones stay in the market.
Well thanks anyway. I'll let you know if I ever find it :p
Could take a while though cause I don't have that much spare time to look at it.

---

### Post by loserboy on 2007-02-07
:)

well post anything new you come up with, ill be watching the thread.

---

### Post by coolclassic on 2007-02-08
> **steve.dhondt said:**
> I didn't get much time the last few days to look at this problem, but I did find a few things the other day. First of all, I feel like a complete idiot for not noticing this before, but one of my usb-ports doesn't seem to be working. So by plugging it in a different port at least I got cups to recognize my printer and I got it to install the right ppd file, but it's still not printing.


I am also getting the same problem with an Epson printer this was never an issue untill recently. On reboot the printer is reconised and after configuration is unable to print. To try and reconfigure printer, the printer manager can not find the printer untill reboot and the cycle continues.

Is this an USB issue ?

---

### Post by sheine on 2007-02-10
My Samsung is supposedly installed but wont print with feisty but did with edgy.

---

