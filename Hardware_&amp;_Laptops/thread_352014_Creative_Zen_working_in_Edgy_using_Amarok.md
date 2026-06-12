---
title: "Creative Zen working in Edgy using Amarok"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by bsalt on 2007-02-02
I wrote a new how-to explaining how to install the latest version of Amarok into Ubuntu Edgy.

Check it out here:
[http://thecrosstalk.blogspot.com/2007/01/amarok-music-manager.html](http://thecrosstalk.blogspot.com/2007/01/amarok-music-manager.html)

---

### Post by jimbren on 2007-02-03
Very well written howto.  I got this going a few months ago, but went through so many false starts and attempts that I confused my steps and couldn't put out a howto.  

Now I've bookmarked yours for reference when I break my own installation of Amarok.

jimbo

---

### Post by bsalt on 2007-02-03
> **jimbren said:**
> Very well written howto.  I got this going a few months ago, but went through so many false starts and attempts that I confused my steps and couldn't put out a howto.  

Now I've bookmarked yours for reference when I break my own installation of Amarok.

jimbo

Well thanks! I'm glad I could help.

---

### Post by pacificdrums on 2007-02-06
Wow that was easy, thanks! Now I can use amarok to put music on my zen micro. yay
:guitar:

---

### Post by bsalt on 2007-02-06
> **pacificdrums said:**
> Wow that was easy, thanks! Now I can use amarok to put music on my zen micro. yay
:guitar:

awesome! i'm glad it worked!

---

### Post by alastair lewis on 2007-02-06
Excellent HOWTO, many thanks. I now have v1.4.5 up and running.
One question, which version of libmtp did you use?

I have tried both the repo version (0.0.18) and 0.1.3 from sourceforge, but I'm not getting MTP plugin as an option when I try to configure new media device (Creative Zen Vision:M in my case)
Everything else seems to be in order, and mtp-detect accesses the device without any issues.

Thanks in advance
Alastair

---

### Post by bsalt on 2007-02-06
Alastair, I was using the repo version - libmtp2 ( version 0.0.18 ) - with Amarok 1.4.4. I had actually heard libmtp 0.1.3 will work with the new version of Amarok.

Jon

---

### Post by bsalt on 2007-02-07
> **alastair lewis said:**
> Excellent HOWTO, many thanks. I now have v1.4.5 up and running.
One question, which version of libmtp did you use?

I have tried both the repo version (0.0.18) and 0.1.3 from sourceforge, but I'm not getting MTP plugin as an option when I try to configure new media device (Creative Zen Vision:M in my case)
Everything else seems to be in order, and mtp-detect accesses the device without any issues.

Thanks in advance
Alastair

Alastair,
I've just updated the blog to support Amarok 1.4.5 and newer versions. It appears to have required a newer version of libmtp, as well as libgpod. Let me know if it helps.

[http://thecrosstalk.blogspot.com/2007/01/amarok-music-manager.html](http://thecrosstalk.blogspot.com/2007/01/amarok-music-manager.html)

Jon

---

### Post by alastair lewis on 2007-02-14
Many thanks,

I have ultimately managed to get it all working with openSUSE 10.2 (which carries amarok with mtp support built in).

Having managed that, I should be able to get it working in Kubuntu as well. I would prefer not to jump distro as Kubuntu works for me.

Alastair

---

### Post by bsalt on 2007-02-14
Hey, as long as you've got mtp support going for ya. I actually just upgraded to Feisty herd 3 - which has Amarok with MTP support built in. But I'm sure this thread has some use to people still.

Ciao,
Jon

---

### Post by HilliBilly on 2007-02-18
hi bsalt,

great howto, installation was without any problems very smoothly (i am on ubuntu edgy gnome 2.6.17-11-386). 

but now ... software updates proposes an update from amarok ver 1.4.5.-1 "down" to ver 2:1.4.3. what does this mean? what should i do with this?

---

### Post by bsalt on 2007-02-18
Hey, on step four I mentioned it there, but I did not make it quite obvious. When you are doing the last and final command - "sudo checkinstall" - you need to carefully read the directions. Before you hit enter the third and final time, you need to rename the package name to amarok-built or something other than amarok. Leaving the name the way it wants it will confuse Synaptic, and thus make it think you have an "update" when in fact you do not.

---

### Post by alastair lewis on 2007-02-26
Hi all,

Still having a few peoblems with Kubuntu. I now have Amarok v1.4.3 working with MTP support, but I can't connect to the Zen Vision:M. libmtp works fine.

At this stage in openSUSE, I manually added the device putting the mount point in as it appeared in Konqeror (//camera:creative zen vision M or something similar). This didn't work with Kubuntu.

What is the correct mount point for these devices under Kubuntu?

(Don't like openSUSE as much as Kubuntu, would like to sort this out)

Many thanks

Alastair

---

### Post by chris.olsen on 2007-03-04
when running ./configure in the amarok folder I get an error "Can't find X libraries".

After doing a search for a fix not much comes up.  I couldn't find any "x" libraries.

Thanks

---

### Post by HFlashman on 2007-03-06
Jon,

I'm fairly new to Ubuntu and Linux in general.  I've read your how-to and am fairly familiar with your steps, however I had a question...

I'm running the KDE as my default desktop.  Won't running the apt-get purge amarok mess with KDE?  
I believe that I may have the latest version of libmtp on my system already (from an effort to get gnomad2 to work with my ZenPlus).  How can I tell if I need to recompile and if the version is good, how do I get mtp support in Amarok?

Sorry if these are obvious questions.  I'm been spending a lot of time configuring my system and I don't want to screw anything up...

Thanks in advance

Chris

---

### Post by bsalt on 2007-03-07
Chris, I was writing "sudo apt-get purge amarok" for the ubuntu users with gnome as their primary manager. instead, type "sudo apt-get remove amarok".

The easiest way to tell if you've got it working with libmtp is to open the preferences window of Amarok, and go to Portable Devices, click on the drop-down menu, and see if it says "Generic MTP Device" or something along those lines.


To everyone else still receiving errors, I am still trying to help you with your missing X library problem - I am on my Windows laptop, and do not have my Ubuntu desktop near me at the moment. I will try to help as soon as I've got it available. I am not ignoring you guys.

---

### Post by bob dylan on 2007-03-28
hi everyone!!

well i was following the crosstalk guide but then i ran into a problem when i ran the following command:

sudo apt-get install build-dep amarok

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-dep

please can someone help me!!!

- michael

---

### Post by rossco_50 on 2007-04-03
Hi michael,

I just had the same problem as you when using the build-dep command.

However, when I checked the install guide on the amarok site it advised to use the command without 'install' in the line. this worked for me.

I was able to complete the install successfully.

As a newbie would be interested to know if the 'install' part of this command in the crosstalk how-to was intended offer an advantage over the amarok guide, or just a typo.

Also, another newbie question, can I simple delete the created folders from the desktop once I have finished the process to tidy up?

Cheers,

Ross

---

### Post by Tadhg on 2007-05-05
Just got my Creative Zen V working with Amarok on edgy. Not sure about feisty yet. It's worth the struggle, it makes everything nice and easy.

I was having trouble getting amarok to find the zen, so ill explain how I got it working for anyone in the same boat. 

first apt-get remove amarok and everything with it. Also make sure libmtp is removed.

download libmtp and the new amarok source along with xine-libs. Make sure you have installed libnjb through aptitude. Compile libmtp first,than xine-libs, and than amarok manually as per the Howto. 

This seems to have done it for me. The combination of libnjb installed through the repositories and amarok and libmtp compiled manually gets everything working.

---

### Post by daka on 2007-05-10
Hi 

I am having some difficulty getting Amarok working with the device.  I am not really proficient in Linux although I seem to be installing distro updates lots.

Can someone verify that I don't have to do anything with repositories in Feisty... it sounds like it should work out of the box.

I am not able to configure the device in Amarok or Connect to it.  When I am asked for the "pre-connect command" and post-connect command I am not sure what to put for these... i.e. mount/__________  eject___________

I also don't know what to put for the "mount point of the device" when asked when configuring media i.e.  mnt/_______________

I suspect the problem is my limited experience, but I do have experience with forums and usually can resolve my problem with a little help.

Many Thanks


Daka

---

### Post by catdriver on 2007-05-15
> **daka said:**
> Hi 

I am having some difficulty getting Amarok working with the device.  I am not really proficient in Linux although I seem to be installing distro updates lots.

Can someone verify that I don't have to do anything with repositories in Feisty... it sounds like it should work out of the box.

I am not able to configure the device in Amarok or Connect to it.  When I am asked for the "pre-connect command" and post-connect command I am not sure what to put for these... i.e. mount/__________  eject___________

I also don't know what to put for the "mount point of the device" when asked when configuring media i.e.  mnt/_______________

I suspect the problem is my limited experience, but I do have experience with forums and usually can resolve my problem with a little help.

Many Thanks


Daka

I had similar questions, and then poked around and thusly learned....
1 You don't need a mount point or a dismount command.
2 Settings > Configure Amarok > Media Devices; set the plugin to <MTP Media Device> with the add device menu choose MTP device.  It should find it from there.
3 for some reason when looking through  system > preferences > hardware information you will find the player on a usb bus identified as a camera, possible because it handles video and photos... I dunno but that may be why it never shows up on a /media/xxx location.

Hope this is helpful.  Mine is up and running.  You can (need to) use the libmtp5, libmtp-dev, libnjb, libnjb-dev, and Amarok straight out of the repos.  These don't appear to be native to 7.04 as some imply... it worked for me, on Feisty 7.04.  Trying to compile from source just made my head hurt as things failed all over.. repeatedly.
Chris (who has been through the ringer for the last four days getting this machine upgraded) ](*,)

---

### Post by chris.olsen on 2007-05-18
catdriver

I don't think I could type "thank you" enough times without a few of my fingers falling off.  I tried all the steps before and I ran into problems, but your solution worked perfectly.

You rock

---

### Post by catdriver on 2007-05-18
> **chris.olsen said:**
> catdriver

I don't think I could type "thank you" enough times without a few of my fingers falling off.  I tried all the steps before and I ran into problems, but your solution worked perfectly.

You rock
It frequently amazes me when the simple solution works (and I find it..), especially with computers.  The rest was mostly trial and error... Happy, as always, to pass on what acorns this blind squirrel can find.

---

