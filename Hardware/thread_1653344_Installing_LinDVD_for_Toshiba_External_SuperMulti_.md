---
title: "Installing LinDVD for Toshiba External SuperMulti Drive"
date: 2010-12-26
forum: Hardware
---

### Post by juliarain on 2010-12-26
[_X-Posted at Multimedia & Video_]("http://ubuntuforums.org/showthread.php?t=1653189")

I'm having the same problem _[this guy]("http://ubuntuforums.org/showthread.php?t=1388106&highlight=lindvd")_  had. He got an error message when trying to install LinDVD, but since  he realized he didn't actually need the software in the first place, the  thread is still unsolved. 

My computer has no CD/DVD drive. I just got a Toshiba External  SuperMulti Drive that I want to use for reading CDs and DVDs. The drive  included a CD with LinDVD on it, which I can put into the drive and use  to install LinDVD. However, the Package Installer gives me the same  status message as CKMBDavis had: [COLOR=Red]**Error: Wrong architecture 'lpia'**[/COLOR]. 

I tried just hooking up the drive to my computer and inserting a DVD. It  prompted me to open Movie Player, which I did, but when it tried to  actually play the DVD, a pop up box came up that said, "An error  occurred. Could not read from resource." VLC will not play the DVD  either. 

Here is my output for print architecture in response to adam814's first comment on CKMBDavis's thread: 

```
$ dpkg --print-architecture
i386
```

I also tried adam814's suggestion in his second comment: 

```
$ dpkg --force-architecture -i <lindvd.deb>
bash: syntax error near unexpected token `newline'
```

How do I get my DVD player to work?

---

### Post by Dark_Stang on 2010-12-26
Sooo... you want to use LinDVD to play movies? Why not just use Totem or VLC?

---

### Post by juliarain on 2010-12-26
As I mentioned above, Movie Player (aka Totem) will not play DVDs from my drive, and neither will VLC.

---

### Post by juliarain on 2010-12-29
[XPosted]

I emailed Corel Customer Service about my LinDVD problem. 

This is their response: 


[INDENT] [I]Dear [omitted] ,


Thank you for contacting Corel Customer Support Services.

Your  program is no longer supported via telephone or through this email   service.  Technical support for your program is available at the   following link only:

Peer to Peer newsgroup forums [http://www.corel.com/newsgroups](http://www.corel.com/newsgroups)

InterVideo-Ulead User to User Web Board [http://phpbb.ulead.com.tw/EN/](http://phpbb.ulead.com.tw/EN/)

Currently Supported Products:
[http://support.corel.com/scripts/rightnow.cfg/php.exe/enduser/std_adp.php?p_faqid=759582](http://support.corel.com/scripts/rightnow.cfg/php.exe/enduser/std_adp.php?p_faqid=759582)

If  you would like information about upgrading your existing product to  the  current version, please contact us via telephone.  A full listing  of  contact numbers can be found at:

[http://support.corel.com/scripts/rightnow.cfg/php.exe/enduser/std_adp.php?p_faqid=754347](http://support.corel.com/scripts/rightnow.cfg/php.exe/enduser/std_adp.php?p_faqid=754347)


Regards,
[omitted]
Corel Customer Support
[/I][/INDENT]

There is no peer-to-peer newsgroup forum for LinDVD. 
The word "LinDVD" is not contained in any post on the User Web Board. 
And why does that full listing of contact numbers not include any United States numbers? 

So here's the deal: I need to screen DVDs for my job (I work at a  library). Failing that, I need to at least screen these things online.  My Netflix subscription doesn't work with Linux. And contrary to popular  belief, not everything is on Youtube, or even on the internet (at least  not where I can find it). 

So it looks like I'm in the market for a new computer. And if I'm going  to keep paying for Netflix (which I need anyway to get those DVDs), that  computer might as well have Windows on it. And if it's going to have  Windows, it might as well have Microsoft Office 2007 on it, so I can  move documents from home to work and vice versa without having the  formatting get screwed up. 

I am extremely angry right now.

---

### Post by hellolife on 2011-06-09
I am also having the same issues, only do not possess LinDVD (or even remember seeing it, or even know what that is).

I am able to use the drive for certain things, like installing Fedora for example. However, any time I put in a dvd, there is no response from my computer whatsoever. I can hear the drive making "loading" noises, but after about a minute these noises subside, and then there is nothing. The dvd nor drive show up on my computer, either.

It would be greatly appreciated if anyone had any advice in this matter.

Thanks!

---

