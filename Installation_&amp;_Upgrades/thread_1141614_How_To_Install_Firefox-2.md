---
title: "How To Install Firefox-2"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by Amish_Gramish on 2009-04-28
I have wanted to kill the person behind making Firefox-3 the default web browser for Ubuntu ever since they made the decision.
I have never had a good experience with F-3, so I installed Firefox-2 in Ubuntu 8.10.

And that brings me to today.
Someone made removed firefox-2 from the Synaptic Package Manager, so I  have been having no luck whatsoever in installing F-2 in Ubuntu 9.04.  I have tried for hours trying to figure out how to install it, and it has come to no avail.

Please, before I take a bat to this computer, will someone tell me how to install Firefox-2?

---

### Post by supererki on 2009-04-28
[http://www.mozilla.com/en-US/firefox/all-older.html](http://www.mozilla.com/en-US/firefox/all-older.html)

---

### Post by Amish_Gramish on 2009-04-28
> **supererki said:**
> [http://www.mozilla.com/en-US/firefox/all-older.html](http://www.mozilla.com/en-US/firefox/all-older.html)

That does not help me out in one bit.

I already downloaded the file, but I have been having a lot of problems trying to install it.

I will reiterate my question:
How do I install Firefox-2.

---

### Post by giantoz on 2009-04-28
you got a tar.bz2 file from the mozilla site right?  you need to compile it from source.  first you need to 

```
sudo aptitude install build-essential
```

then extract the firefox2 source, open the terminal and cd to where you extracted the firefox2 source

```
./configure
```
```
make
```
```
sudo make install
```

---

### Post by SuperSonic4 on 2009-04-28
You can also unpack it and run the firefox script locally from the extracted folder. This way you can have firefox 2 and 3 both installed.

Bear in mind Firefox 2 is no longer supported by Mozilla:

> 

Firefox 2.0.0.x will be maintained with security and stability updates until mid-December, 2008. All users are strongly encouraged to upgrade to Firefox 3.

---

### Post by giantoz on 2009-04-28
To SuperSonic4:

love your avatar.  Best Maiden song IMO.

---

### Post by Amish_Gramish on 2009-04-28
> **giantoz said:**
> you got a tar.bz2 file from the mozilla site right?  you need to compile it from source.  first you need to 

```
sudo aptitude install build-essential
```

then extract the firefox2 source, open the terminal and cd to where you extracted the firefox2 source

```
./configure
```
```
make
```
```
sudo make install
```

I unpacked the firefox-2.0.0.20.tar.gz file to ./Desktop/Install/, and I cd'd to ./Desktop/Install and it won't let me do anything else.

```
xxxx@computer:~$ cd ./Desktop/Install
xxxx@computer:~/Desktop/Install$ ./configure
bash: ./configure: No such file or directory
```

Apparently ./configure isn't helping me whatsoever.
What do I do?

(And I know there won't be security updates, yada yada yada, but the plain moronic things that were implemented into Firefox 3 just make me want to kill people.  I want to meet the guy that combined the back pages and forward pages into one "recent pages" thing, because I find that just as stupid as having something telling you to press the start button when you want to play the game.  I already turned my console on and put in the game disc, why would I want to waste another ten seconds of my life a couple times a day?
And Firefox 3 likes to think that right clicks means I want to bookmark pages, save pages, open pages in new windows, bookmark images, etc.
Oh, the anger runs through my veins.)

---

### Post by Amish_Gramish on 2009-04-28
Anyone want to take a crack at this?

---

### Post by ninjapirate89 on 2009-04-28
Is there no way (though use of plug-ins, settings, etc) to make F3 behave the same as F2? What in particular do you not like about F3? You could go from there to figure out how to revert or disable those features. That way you could have the security of F3 and the behavior of F2.
(I don't know if this can actually be done, it's just an idea)

---

### Post by aysiu on 2009-04-29
Firefox 2 was removed because it is no longer supported. It does not receive security updates any more.

First, [make sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources)

Then, assuming the Firefox .tar.gz file is on your desktop, paste these commands in the terminal to get Firefox 2 installed: ```
sudo apt-get update
sudo apt-get install libstdc++5 firefox
cd ~/Desktop
sudo tar -xvzf firefox-2.0.0.20.tar.gz -C /opt
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
``` If you're going to use Firefox 2, I would highly recommend you install the NoScript extension, as that will probably make up for the lack of security updates.

---

### Post by Amish_Gramish on 2009-04-29
> **ninjapirate89 said:**
> What in particular do you not like about F3?

When I right click it likes to do weird things.
Sometimes it tries to bookmark a page, a link, a picture, etc., sometimes it opens a link into another tab, sometimes it opens them in a new window, sometimes it tries to send an e-mail, sometimes it tries to save the link, and that's just the stuff I can remember off hand.
That's my main problem.

The same thing happened in Ubuntu 8.10 and 8.04, but at least now it doesn't try to open websites with something I highlighted, searched, clicked, etc. in the name.  (Only 3.0 did that in 8.04, then Firefox 3 and Firefox 2 did that in 8.10.  I'm glad 3 doesn't do it anymore.)  (An example of this is I would search "firefox-2" in Google and ten minutes to half an hour later it would load up [http://www.firefox-2.com](http://www.firefox-2.com), but only after it loaded old links I clicked a little earlier than that or when I typed "farting panda" into YouTube.)

Good times, especially because it did this at random.
It did that twice while I was taking a 20 minute online test for college.  Luckily I was somehow able to continue taking the test.

And I can't find anything to get it to stop messing with the right click.

---

### Post by aysiu on 2009-04-29
> **Amish_Gramish said:**
> When I right click it likes to do weird things.
Sometimes it tries to bookmark a page, a link, a picture, etc., sometimes it opens a link into another tab, sometimes it opens them in a new window, sometimes it tries to send an e-mail, sometimes it tries to save the link, and that's just the stuff I can remember off hand.
That's my main problem.

The same thing happened in Ubuntu 8.10 and 8.04, but at least now it doesn't try to open websites with something I highlighted, searched, clicked, etc. in the name.  (Only 3.0 did that in 8.04, then Firefox 3 and Firefox 2 did that in 8.10.  I'm glad 3 doesn't do it anymore.)  (An example of this is I would search "firefox-2" in Google and ten minutes to half an hour later it would load up [http://www.firefox-2.com](http://www.firefox-2.com), but only after it loaded old links I clicked a little earlier than that or when I typed "farting panda" into YouTube.)

Good times, especially because it did this at random.
It did that twice while I was taking a 20 minute online test for college.  Luckily I was somehow able to continue taking the test.

And I can't find anything to get it to stop messing with the right click.
It sounds as if something is wrong with your mouse configuration.

That is not normal behavior for Firefox 3.

I don't think installing Firefox 2 will help solve your problem.

---

### Post by Amish_Gramish on 2009-04-29
> **aysiu said:**
> It sounds as if something is wrong with your mouse configuration.

That is not normal behavior for Firefox 3.

I don't think installing Firefox 2 will help solve your problem.

It helped with Ubuntu 8.10.
It never did that with Firefox 2, but did it all the time with Firefox 3.
And I have to uninstall Firefox 3 first, right?

---

### Post by aysiu on 2009-04-29
It definitely sounds as if your mouse is too sensitive. When you try to right-click, it's actually right-clicking and then "right"-clicking again on one of the context menu options.

If you think having 2 installed will help, follow the instructions I gave you on the previous page. You should keep 3 installed, though, for the instructions to work.

---

### Post by asbesto on 2009-04-29
> **Amish_Gramish said:**
> (And I know there won't be security updates, yada yada yada, but the plain moronic things that were implemented into Firefox 3 just make me want to kill people.  I want to meet the guy that combined the back pages and forward pages into one "recent pages" thing, because I find that just as stupid as having something telling you to press the start button when you want to play the game.  I already turned my console on and put in the game disc, why would I want to waste another ten seconds of my life a couple times a day?
And Firefox 3 likes to think that right clicks means I want to bookmark pages, save pages, open pages in new windows, bookmark images, etc.
Oh, the anger runs through my veins.)

I quote you 100%. You're damn right! :(

---

### Post by asbesto on 2009-04-29
> **Amish_Gramish said:**
> When I right click it likes to do weird things.
Sometimes it tries to bookmark a page, a link, a picture, etc., sometimes it opens a link into another tab, sometimes it opens them in a new window, sometimes it tries to send an e-mail, sometimes it tries to save the link, and that's just the stuff I can remember off hand.
That's my main problem.

And I can't find anything to get it to stop messing with the right click.

Same problem here. I think this happens on "slow" computers. Thinkpad T40 here, Firefox3 is "like Godzilla fainting on a 103 years old pregnant woman", as a friend of mine like to say. :)

I noticed this:

1) i right-click
2) time passes, and
3) the menu start appearing
4) I release the right-click.

Time is variable, so when releasing, the menu is going on screen, and so the release "pick up" something: download of image, search, whatsoever.

I can only stop this in this way:

1) right-click, and hold
2) time passes
3) wait for the complete menu's appearing
4) choose the command I want
5) RELEASE the right click.

When the DAMN FIREFOX into the DAMN ubuntu 9.04 stop swapping and digging 100% of my CPU, after some seconds (10, 20, 30 seconds sometimes!!!) I'm able to choose the menu options.

It's a damn problem. UBUNTU is growing in stupidity, lazyness, adding unstability and taking no care of users with "old" hardware. I'm using a Thinkpad T40, I upgraded to 9.04, my xorg now is slow like a 386dx-25 without coprocessor. 

But that's another problem... hope my message can help you!

P.S. A hint: Try to recover firefox 2 package from ubuntu 8.10 cdrom! :) 

I now will reinstall the 8.10 (to get rid of the 9.04 sh1t) and will FIX the package in apt config files, to not have the damn ff3 installed. 


What a problems! Developers? why they don't care about users and this forum? BOOH!

---

### Post by dballanc on 2009-04-29
I've had the exact same experiences with right click misbehaving.  It doesn't do it in other applications.  95% of the time everything works normally, but eventually something breaks.  If I hold down the right click and select the menu options, then release they are still usable.  But before I notice I usually end up with a few random evolution 'send link' windows, or new windows.  Pretty much identical to what asbesto describes.

I've tried other mice to make sure it wasn't a stuck, just using touchpad, etc.  Same problem.  When it 'breaks', it breaks on every click there after until firefox is completely restarted... but I can use it for hours or even days before it 'breaks'.

Epiphany has been a good alternative, but it's hard to do without a few of the plugins.

---

### Post by aysiu on 2009-04-29
Hm. I thought at first it was a mouse problem, but it appears to be something Firefox-related. I'm not sure why it affects only some users and not others.

There is a bug report on it already: [[MASTER] right click (with button release) might activate random popup-menu-item](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313)

The status as of last week was *firefox-3.0 (Ubuntu) status: Triaged &#8594; In Progress *

---

### Post by Amish_Gramish on 2009-04-30
> **aysiu said:**
> Hm. I thought at first it was a mouse problem, but it appears to be something Firefox-related. I'm not sure why it affects only some users and not others.

There is a bug report on it already: [[MASTER] right click (with button release) might activate random popup-menu-item](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313)

The status as of last week was *firefox-3.0 (Ubuntu) status: Triaged &#8594; In Progress *

Huh, I didn't think it warranted a bug report, because I hadn't heard of it on any other computers.

And as tastey asbestos said, it looks like this happens on slow computers, as my computer is a Compaq F572US (two years old and 1.8 GHz AMD 64).

At the bottom of the comments, someone said that there's a patch set for Firefox 3.0.0.10 that fixes this (kind of very, very sad that people have been reporting on this for over a year), so if I can't get Firefox-2 installed, I guess I'll just have to wait.

Thanks for all the help (both with installing Firefox-2 and letting me know I'm not alone in this "right click (with button release) might activate random-popup-menu" thing)!

---

### Post by aysiu on 2009-04-30
> **Amish_Gramish said:**
> 
And as tastey asbestos said, it looks like this happens on slow computers, as my computer is a Compaq F572US (two years old and 1.8 GHz AMD 64). It's not all slow computers. I have an underclocked 900 MHz Celeron processor, and no problems with Firefox 3.

---

### Post by Amish_Gramish on 2009-05-01
> **aysiu said:**
> It's not all slow computers. I have an underclocked 900 MHz Celeron processor, and no problems with Firefox 3.

Whatever the problem is, I guess I'll just have to wait for Firefox 3.0.0.10 to release, as I've tried to get Firefox 2 running (I did one time, but it just wouldn't connect to the internet).

I had my HDD backed up, so it's all good.

Thanks for the help anyways!  (If it doesn't get fixed, I think I may just go back to 8.10.)

---

