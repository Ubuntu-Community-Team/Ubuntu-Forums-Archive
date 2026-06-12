---
title: "TweetDeck"
date: 2008-10-23
forum: General Help
---

### Post by jdorenbush on 2008-10-23
I am trying to install TweetDeck on 64bit Ubuntu. I am having some problems.

I followed these steps. [http://www.kozaru.net/2008/08/12/adobeair-alpha-on-ubuntu-64-bit/](http://www.kozaru.net/2008/08/12/adobeair-alpha-on-ubuntu-64-bit/)

> 1. Download and extract the AdobeAIR SDK. Put it somewhere nice. I put it in /home/michael/AdobeAIR.

2. Pick an AIR app and download it. I used TweetDeck cos it&#8217;s what I wanted.

3. A .air file is just a zip file, so with your favourite unzipper, unzip it somewhere nice. I used /home/michael/AdobeAIR/apps/tweetdeck

4. Make a script file, in this case called tweetdeck.sh

5. Put the following into this file:
/home/michael/AdobeAIR/bin/adl -nodebug /home/michael/AdobeAIR/apps/tweetdeck/META-INF/AIR/application.xml /home/michael/AdobeAIR/apps/tweetdeck

In short, PATH TO ADOBEAIR, with -nodebug switch, PATH TO AIR APP (/META-INF/AIR/application.xml is the same for every app), PATH TO AIR APP BASE DIRECTORY (very important). This should all be on one line!!

6. Save the file and make it executable, either in console with chmod +x ./tweetdeck.sh or by right clicking and following the tabs.

7. Run the file and enjoy the AIR. You can add this file to your favourite panel or launcher.

This is what my setup looks like after following those steps:
/home/jeff/src/AdobeAIRSDK
/home/jeff/src/tweetdeck
/home/jeff/src/tweetdeck/tweetdeck.sh
```
/home/jeff/src/AdobeAIRSDK/bin/adl -nodebug /home/jeff/src
/home/jeff/src/tweetdeck/META-INF/AIR/application.xml
/home/jeff/src/tweetdeck
```
  - Made Executable

When I try and run it either through the launcher I created or the SH file itself - nothing happens.

---

### Post by phidia on 2008-10-23
I'm not familar with that app but have you tried running it in a terminal?
Open a terminal, cd to directory containing executable, type ./tweetdeck or sh tweetdeck.

Post output?

---

### Post by jdorenbush on 2008-10-23
> **phidia said:**
> I'm not familar with that app but have you tried running it in a terminal?
Open a terminal, cd to directory containing executable, type ./tweetdeck or sh tweetdeck.

Post output?

```
sh: Can't open tweetdeck
```

I don't think I created the SH file properly. What are the steps to creating an SH file?

---

### Post by phidia on 2008-10-24
The link you provided in your 1st post here isn't working. What does the INSTALL or README say?

---

### Post by jdorenbush on 2008-10-24
> **phidia said:**
> The link you provided in your 1st post here isn't working. What does the INSTALL or README say?

Fixed link.

From [TweetDeck]("http://www.tweetdeck.com/beta/")
> TweetDeck requires the Adobe Air runtime be installed first.
Then download the TweetDeck AIR file

...thats all I get for "instructions".

---

### Post by phidia on 2008-10-24
I see that tweetdeck is beta-bugs can be expected. There's a blog about it [here]("http://flanture.blogspot.com/2008/08/air-based-twitter-application-tweetdeck.html"), but that won't be very helpful to you. 
Maybe there is a irc chat you can login to get help?

---

### Post by jdorenbush on 2008-10-28
> **phidia said:**
> I see that tweetdeck is beta-bugs can be expected. There's a blog about it [here]("http://flanture.blogspot.com/2008/08/air-based-twitter-application-tweetdeck.html"), but that won't be very helpful to you. 
Maybe there is a irc chat you can login to get help?

Bummer. I guess I am on my own for this.

---

### Post by deluzione on 2008-11-11
I have the problem too with Ubuntu Intrepid 64.

When I start Tweetdeck in the Terminal it says this:
> libgnome-keyring.so: cannot open shared object file: No such file or directory

Any thoughts?

---

### Post by diffuze on 2008-11-15
TweetDeck works like a charm for me but I have a 32 bit system.
Regarding Adobe AIR that needs to be installed first; this is what the download site says: "Installation on 64-bit distributions is not supported in this release." So that might be the issue.
Anyway, the simple instructions are:
1. Download Adobe AIR from [http://labs.adobe.com/downloads/air_linux.html](http://labs.adobe.com/downloads/air_linux.html) - direct link to file: [http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_b1_091508.bin](http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_b1_091508.bin)
2. Make this downloaded file executable
3. Download the TweetDeck AIR file: [http://www.tweetdeck.com/beta/TweetDeck_0_19_3.air](http://www.tweetdeck.com/beta/TweetDeck_0_19_3.air)
4. Install Adobe AIR. Preferably run sudo ./adobeair_linux_b1_091508.bin
Just follow instructions. I kept all default settings.
5. Run the TweetDeck AIR file, after TweetDeck is installed all that should be needed is to click on it in nautilus. Follow instructions.
6. Enjoy.

---

### Post by b33god on 2009-01-10
I have also been struggling to get TweetDeck working on 64bit Hardy Heron for  a number of months.  I followed steps here [http://www.kozaru.net/2008/08/12/adobeair-alpha-on-ubuntu-64-bit/](http://www.kozaru.net/2008/08/12/adobeair-alpha-on-ubuntu-64-bit/) to try a workaround using the Air SDK but experienced the same issue.

On seeing the error libgnome-keyring.so: cannot open shared object file: No such file or directory  I simply used getlibs (which I already had installed) to grab the missing 32bit library

```
sudo getlibs -l libgnome-keyring.so
```

Still no luck - TweetDeck seems to be looking for libgnome-keyring.so.0

Ok then - ```
sudo getlibs -l libgnome-keyring.so.0
```

still no work so I look in the lib32 folder and see that libgnome-keyring.so.0 is a broken simlink linking to the non-existant libgnome-keyring.so.0.1.1 so I try
```

sudo getlibs -l libgnome-keyring.so.0.1.1
```

this fixed the simlink. On running my shell script to start the SDK TweetDeck workaround it pops up asking for Twitter logon details and in I go, perfect.

I have since tried the normal install of air and tweetdeck and that now also works fine so it seems I only needed to grab the correct libs in the first place.

---

### Post by madverb on 2009-03-04
Just did it then. Thought this might be handy if anyone else needs some help soon.

First...
[http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb408084)

Second...
[http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu](http://www.ossramblings.com/tweetdeck_in_64_bit_ubuntu)

---

### Post by crashnburn007 on 2009-04-13
I’m unable to find the tweetdeck sqlite db directory in ubuntu/linux
any ideas?
I found…
/opt/TweetDeck/share/META-INF/AIR/tweetdeckfast.f9107117265db7542c1a806c8db837742ce14c21.1.directory
but when I try to open it says it’s not a folder :S

---

### Post by emaillenin on 2009-09-27
[]("http://us.lrd.yahoo.com/_ylt=AqqDAxMZlFJct52n27.269Z0fNdF/SIG=11495msj6/**http%3A//emaillenin.blogspot.com/")Install TweetDeck in Ubuntu in three easy steps.
				 TweetDeck installation in not an easy one-click installation in any Linux. Follow these three steps and get the latest version of Adobe AIR and TweetDeck in your system in five minutes

[http://emaillenin.blogspot.com/2009/09/install-tweetdeck-in-ubuntu-in-3-steps.html](http://emaillenin.blogspot.com/2009/09/install-tweetdeck-in-ubuntu-in-3-steps.html)

---

### Post by davie on 2010-06-15
Big thanks to Emaillenin. That worked for me with no problems.

---

