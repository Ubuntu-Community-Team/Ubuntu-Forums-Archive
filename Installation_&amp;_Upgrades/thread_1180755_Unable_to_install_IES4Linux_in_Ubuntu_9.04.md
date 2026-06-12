---
title: "Unable to install IES4Linux in Ubuntu 9.04"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by H.K.Murmu on 2009-06-07
I have tried several time to install ies4linux  but every time it shows error.


while installing error coming is--- mfc42.cab    no such file in the directory

i am using ubuntu 9.04, wine 1.1.23 , cab extract 1.2-3


please help me

---

### Post by riteman on 2009-10-25
I have same Kind of problem:
When running ie4linux using the GUI it seems no data get downloaded so I found all CAB files and threw them in the downloadfolder.
Then started the installation without GUI and without flash installation - every time it tells me that VGX.CAB is corrupted. I tried to download from several different FTP sites so I am sure there is another problem here.:confused:

I use Wine 1.0.1 

Here the output from ies4linux when run in the terminal
 
ebay@ebay-laptop:~/Desktop/ies4linux-2.99.0$ ./ies4linux --no-gui --no-flash
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

IEs4Linux will:
  - Install Internet Explorers: 6.0
  - Using IE locale: EN-US
  - Install everything at: /home/ebay/.ies4linux
[ OK ]

Downloading everything we need
  Downloading from microsoft.com:
   0%   249973USA8.exe   ADVAUTH.CAB
   CRLUPD.CAB
   HHUPD.CAB
   IEDOM.CAB
   IE_EXTRA.CAB
   IE_S1.CAB
   IE_S2.CAB
   IE_S5.CAB
   IE_S4.CAB
   IE_S3.CAB
   IE_S6.CAB
   SETUPW95.CAB
   FONTCORE.CAB
   FONTSUP.CAB
   VGX.CAB
An error ocurred when downloading. Please run IEs4Linux again. Corrupted file: ie6/EN-US/VGX.CAB
VGX.CAB then gets deleted.

It seems the homepage for ie4linux has been blocked?

---

### Post by riteman on 2009-10-25
I also changed timeout values for wget as suggested here:
[http://tehpost.blogspot.com/2008/06/ie4linux-download-problem-during.html](http://tehpost.blogspot.com/2008/06/ie4linux-download-problem-during.html)

No luck :(

---

### Post by motsteve on 2009-10-25
I know I'm going to sound like a weisenheimer, but why would you want IE on Linux?  I would guess that there are legitimate advantages such as introducing someone to Linux and giving them a familiar environment to do it in, but, call me prejudiced towards Firefox,but I'm just not getting it.

---

### Post by swizman on 2009-10-25
I just installed IES4Linux yesterday. 

I got the errors to and each time I force-quit the GUI window and started again. Each time it got further in the install and after about 6 times restarting it finally said OK. 
I opened IE with the command IE6 and it did came up, but I did not further tested it.

I am using Ubuntu 9.10 and tried both WINE 1.0.1 and 1.1.31, no difference.

The tatanka website is blocked, but you still can go there, but all you will find ther is ies4linux-2.99.0.1, which did not changed since about one year.

You can get ies4linux-2.99.0.1 with this command:

wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)


TO motsteve: 

How about you would like to install MS Money with WINE. MS Money is a very popular personal financial software program, and users may have worked and collected data with it for many years.

Now MS Money is really only a bunch of htm scripts, using IE 6 as it's GUI. 
IE 6 can be scripted fully and you will not notice anywhere that it is IE, it gives a very professional looking GUI. 

Many other programs are using the same trick, including the very popular TurboTax.

---

### Post by Mark Phelps on 2009-10-25
If you're really determined to run IE in Ubuntu, check out the Crossover trial at CodeWeavers.  I tried that a few months ago when it was first released because I need IE for some things -- and found the IE7 installation was a disaster!  But, evidently, I was not alone and the CodeWeavers rep told me they were actively working the IE problems and would have a new version out in the Fall that fixed them.

They may have that out now.  It would be worth checking out.

---

### Post by riteman on 2009-10-25
> **motsteve said:**
> I know I'm going to sound like a weisenheimer, but why would you want IE on Linux? I would guess that there are legitimate advantages such as introducing someone to Linux and giving them a familiar environment to do it in, but, call me prejudiced towards Firefox,but I'm just not getting it.
 
Well, I certainly do not like IE6 at all but our CRM system (Siebel) only works with IE6 and it is my dream to be able to use Ubuntu for everything.

---

