---
title: "3com Megahertz 3CCFEM556B problem"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by canargyrou on 2007-04-10
Dear all,

Yesterday my dad wanted to try out Linux. I had installed Ubuntu 6.10 Edgy recently to my desktop and told him to try it out to his laptop.
The problem with my dad's laptop is that it has an onboard ethernet card with problematic plug. The card is recognized correctly (as eth0) but he cannot use it due to the problematic plug. The laptop also has a wireless connection recognized correctly (as eth1) but we don't have wireless lan at home.
The last option available is to use a PCMCIA modem/ethernet card which is a 3Com Megahertz 10/100 LAN + 56k Modem (Model 3CCFEM556B).
It seems that the PCMCIA card is recognized correctly (from the Device Manager) but when we insert it then we don't get an eth2 so we can't configure it.
From what I can tell, dmesg does not give any errors and the card is recognized correctly.
Has anyone any idea where to start looking for problems?

Thanks in advance.

---

### Post by dragomirov on 2007-04-10
If the system recognize your card doesn't mean that the drivers of that card are loaded. In this case you have to look in which way your 3Com card is supported  (native kernel driver, ndiswrapper).

Then if is native supported you have to load the proper module in the kernel ("sudo modprobe <nameofthemodule> ) or look for ndiswrapper [http://ubuntuforums.org/showthread.php?t=31926]("http://ubuntuforums.org/showthread.php?t=31926")
could be helpful
as well as
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

---

### Post by canargyrou on 2007-04-10
Dear dragomirov,

The list of supported hardware for ndiswrapper at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) does not have my hardware, but I'll give it a try in case it works.
I'll come back later and let you know.

Thanks for your help.

---

### Post by canargyrou on 2007-04-11
After looking a little bit more on the internet I found out that pcmcia_cs supports my pcmcia card using the 3c574_cs driver ([http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS)](http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS)).
An lsmod showed that pcmcia_cs and 3c574_cs are loaded.
dmesg does not report any problems.
But ubuntu does not have an eth interface pointing to that card.
Furthermore, my dad installed an older version of SuSe (I believe 9.3) and found out that the card was working (at least the lights of the card) but he couldn't configure the eth interface because yast was hanging every time.
It seems that there is some configuration missing in ubuntu from what I can tell.
Has anyone any idea of what I should look at next?

Thanks in advance.

---

### Post by dragomirov on 2007-04-11
I'm not such wifi expert, just a geek, but I got the same problem as you with my integrated Broadcom card when I was on dapper. The loaded kernel module had to load the card but no eth1 or similar appears on my ifconfig.
The procedure I followed was:
- unload the kernel module (sudo rmmod <modulename>) and put it in the blacklist.
- load the win###s driver with ndiswrapper, even if the card wasn't supported at the time.

It's worth a try, try Feisty also it's less then 3 days to final release.

then buy some :popcorn: and good luck

---

### Post by canargyrou on 2007-04-13
No success yet.

I have tried ndiswrapper but I get an invalid driver error.
I have posted my problem to ndiswrapper forums and wait for any replies.

---

### Post by canargyrou on 2007-04-14
I've got the following answer in ndiswrapper forums:
'This card seems to be 16-bit pcmcia (not cardbus) card; ndiswrapper doesn't support them.'

So, I'm stuck again.
What next?
Some way has to exist that will make the card work...

---

### Post by Whatawonderfulday on 2007-04-15
I posted this on another thread, but it appears to apply here also:

"Perhaps I can shed a little light.

"I'm not too sure about the status of a USB modem, but the following obtains for built-in modems and pcmcia card modems. Starting with kernel 2.6.14, I believe, there was a regression in the kernel so that such modems were not properly handled and it was impossible to set up a modem at all (at least of the types specified). Someone told me that the problem had been sorted out in the 2.6.20 kernel and to wait for that kernel to circulate (in the particular discussion that I had, in Fedora Core--I assume that the fix would appear in any Linux kernel labelled 2.6.20, although I have been trying without success to verify this). The 2.6.20 kernel is now circulating, but in the case of Ubuntu from what I have just seen in the forum, to use that kernel with edgy eft you would have to do a compile, not a trivial matter; otherwise you have to get feisty fawn, which comes 'out of the box' with a version of the 2.6.20 kernel. So as things stand, at least for built-in modems and pcmcia modems such as 3COM 3CXEM556 B, you have to upgrade to feisty fawn. However, I emphasize that I have been unable to get anyone to confirm that the fix for modems has indeed been installed in the 2.6.20 kernel as it appears in feisty fawn. It seems that unless someone clarifies this (please!) it will be necessary to upgrade to feisty fawn using a network or similar and then go off to a telephone to try the modem to see what happens.

"Moreover, part of the reason for the regression is that the code for handling modems was moved into the kernel from external drivers. Hence, with any of the kernels between 2.6.14 and 2.6.20 inclusive, the modem is not properly detected and you are wasting your time with wvdial. Of course if someone was able to use an external modem on his serial port, that is another matter.

"Hope this helps. I sure would appreciate it if one of the techies would clarify this.

"Whatawonderfulday."

The gist of the message is that your dad will get nowhere trying to get his pcmcia modem working until he gets feisty fawn or another Linux distro with kernel 2.6.20, assuming that the fix has indeed been installed in that release of the kernel.

I sure hope that a techie will shed some light on this.

Whatawonderfulday

---

### Post by Whatawonderfulday on 2007-04-17
Here is a clarification of the matter of the pcmcia card problem which I posted on another thread:

I have received confirmation as follows:

"I see that kernel 2.6.20 is circulating. Could you confirm that it contains the fix for this pcmcia card
problem?..."

"yes, it works fine in FC6 since kernel 2.6.20-1.2925.fc6
"see [https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=207910](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=207910)
...

"I see that Ubuntu is distributing kernel 2.6.20 and I assume that any distro which has a kernel labelled 2.6.20 has the fix installed. Is this a reasonable assumption?"

"yes, it's been fixed in 2.6.20-rc1 according to
"[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/52510](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/52510)"

Now in Ubuntu this fixes the pcmcia modem problem with the kernel recognizing the pcmcia card as of Feisty Fawn. Just precisely what happens with an inbuilt winmodem, I cannot say, but it is clear from reading the two bug reports (by different parties) that the problem was with the pcmcia modem. It doesn't appear to me to have been a problem with all modems...


It therefore seems to me that the best thing that your dad could do is install Feisty Fawn and try the pcmcia modem with that.  However, you never know what's going to happen until you try it.

With best wishes--

Whatawonderfulday

---

### Post by Ted Nancy on 2007-05-22
Well, I'm using feisty now (xubuntu 7.04) and can't seem to get the 3COM 3CCFEM556 B ethernet / modem working at all. 

I don't even care about the modem, just the ethernet. it seems like your last post suggested this bug:

[https://bugs.launchpad.net/fedora/+bug/52510](https://bugs.launchpad.net/fedora/+bug/52510)

would be fixed.

Any help is appreciated.

---

### Post by Whatawonderfulday on 2007-05-23
To Mr Nancy:

I am sending this under Feisty Fawn using the 3COM modem in its dial-up mode.  When I installed Feisty and went to use the pcmcia modem, it didn't work.  The reason was that the file

3CXEM556.cis

has to be installed in /lib/3CXEM556.cis.

Now where are you going to get this file?  If you have a previous installation of Ubuntu or other Linux where the pcmcia card worked, you can simply take a copy of the file in the location specified, and then install it in the location given once you install Feisty--where you store the file depends of course on the particular configuration you have.  You might need to use external media.

I haven't yet had the opportunity to use the card with the LAN network connection, although Feisty continually brings up both the native LAN eth0 connection and the LAN eth1 connection on the card.  You are of course aware that the card LAN connection has only a 10MB rating.  Such a rating is not compatible with a 100MB line.  But I suppose that apart from that, if you install the .cis file, you should be okay--although stranger things have been known to happen than that LAN part of the card might not work.  If you still have problems, reply and I'll see what I can do to find out what has to be done for the LAN part of the card.

With best wishes--

Whatawonderfulday

---

### Post by jcpeart on 2007-07-08
I am trying to install Feisty on to an old laptop from the "alternate" disk.  I got to the part where it is trying to detect network hardware and it tells me that "no network interfaces were found"  I am using the 3COM 3CXEM556B pcmcia card.  Windows 2000 installs on this machine and recognizes the card as did puppy linux last year.

---

### Post by Whatawonderfulday on 2007-07-09
To jcpeart:

I doubt I can tell you anything, but I have not had a problem with Ubuntu 7.04 recognizing the pcmcia card's LAN component.  It comes up as ethernet1, where ethernet0 is my inbuilt ethernet connection.

I wonder if you have connected the card to a 100MB line, where the card is rated at 2MB.  These cards cannot work with a 100MB line.  But of course you may know that and it may have nothing to do with your problem.

I've never bothered to use the pcmcia card for LAN since I already have ethernet0 and only connect to a 100MB line when I am using LAN.  But I think it works.

You might try resetting the pcmcia card to its factory settings.  The way to do this is to install the card somewhere on Windows and then using the network connection pre-initialization console, execute Z3 (standard) or Z4 (forces hardware error control).  Of course, this might be resetting the factory defaults only for the modem part of the card.

There's always the 'reinsertion maneuver', but you have probably already done that.  Take the card out and put it back in.

I wonder what the problem might be, since the card works, as you say on W2K and on puppy.  It works for me on 7.04.

Best of luck--

Whatawonderfulday

---

