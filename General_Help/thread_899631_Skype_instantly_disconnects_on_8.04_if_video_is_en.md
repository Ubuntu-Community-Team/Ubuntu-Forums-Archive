---
title: "Skype instantly disconnects on 8.04 if video is enabled"
date: 2008-08-24
forum: General Help
---

### Post by myotis on 2008-08-24
Anyone any ideas on this one. Its a Logitech 9000 and a Matrox P650 video card with the latest drivers from Berlios.

When the receiver answers the Skype call, they get a second of video and then Skype disconnects. The audio seems to work fine, if you disable the  video.

I've already asked several times about issues with getting the video test to work with Skype, but obviously, no one can help me with that one as  no one has replied,  but I mention it again to see if it gives a clue with this problem.

It all worked with 7, but not with 8.

Graham

---

### Post by myotis on 2008-08-25
To add to this, I have now downloaded Skype from the Medibuntu repository and tried the three different options.

Only the standard install gives me a video preview, albeit just a blur of colours which you can just about make out some movement through the blur.

The other two options give no preview and crash if you try and test it.

So I have stuck with the standard medibuntu install as the downlaod from Skype needed you to edit the video resolution in the config file to stop it the video test from crashing Skype. So I am assuming the Medibuntu version has some customisation for Ubuntu.

However, the instant disconnect still persists, except there is no longer a glimpse of video, it just disconnects when the recipient accepts the call.

Graham

---

### Post by Claus7 on 2008-08-26
Hello,

I faced a lot of problems installing skype in dapper, because the deb packages where not available for this version. The bad thing about these, is that you cannot change anything during the installation, so if something goes wrong you cannot avoid it (according to my humble experience). 
On the other hand, if you compile a program for yourself you have the ability to give some options so as the installation to fit to your system's needs. What I would propose you is to test also the dynamic and static versions of skype and see if they are working better for your system. 
It might be a bug in skype package, yet in other sytems with hardy on them is working flawlessly. So install the version I'm proposing you for yourself and see if it has any difference.
Another idea should be to check your camera with another program and see if it is working. If, as you say, a camera model is working flawlessly with hardy, then doing that you can check whether is a skype bug or not. May be some better version in the future might solve that problem.
Maybe not some permanent solutions, yet rather some ideas that might help you.

Regards!

---

### Post by myotis on 2008-08-26
> **Claus7 said:**
> Hello,
On the other hand, if you compile a program for yourself you have the ability to give some options so as the installation to fit to your system's needs. What I would propose you is to test also the dynamic and static versions of skype and see if they are working better for your system. 
It might be a bug in skype package, yet in other sytems with hardy on them is working flawlessly. So install the version I'm proposing you for yourself and see if it has any difference.
Another idea should be to check your camera with another program and see if it is working. If, as you say, a camera model is working flawlessly with hardy, then doing that you can check whether is a skype bug or not. May be some better version in the future might solve that problem.Regards!

Thanks for the reply. I have already tried all three versions of Skype that come with the Medibuntu repository (I assume that is what you mean by static and dynamic) and only the standard install didn't exit when testing the camera.

The camera is working fine with Cheese and Ekiga, so it seems restricted to Skype.

Looking at the Skype support forum others are having the same problem - worked fen with Ubuntu 7, broken with Ubuntu 8.

I guess I just have  to wait for a fix, either in Ubuntu or in Skype. 

Thanks again,

Graham

---

### Post by myotis on 2008-08-26
Just to follow this up if anyone is watching I have now upgraded the Pulse audio as per this post to see if that helps as it has been suggested that this could be part of the problem.

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

It hasn't made any difference. Actually that isn't true, it isn't now disconnecting, but I'm getting no video.

Graham

---

### Post by Claus7 on 2008-08-27
Hello,

> **myotis said:**
> I have already tried all three versions of Skype that come with the Medibuntu repository (I assume that is what you mean by static and dynamic) and only the standard install didn't exit when testing the camera.


Not exactly. This is not what I mean. What I mean is go to the skype site and there under the various linux versions, it has also a dynamic and a static package. Download one for your system, extract the folder, go inside that folder, compile for yourself and do the installation (configure - make -make install). In the process see if it has any specific options that you might have to put manualy for your camera. 
I have not hardy at the moment so I do not know about the available versions that the medubuntu repository gives you. Just do it for a test. I think that having tried all the things you say this would be a minor effort. 
Other than that is seems that it is a malfunction with the specific camera so in a future version this might be solved.

Regards!

---

### Post by myotis on 2008-08-27
> **Claus7 said:**
> Hello,



Not exactly. This is not what I mean. What I mean is go to the skype site and there under the various linux versions, it has also a dynamic and a static package. Download one for your system, extract the folder, go inside that folder, compile for yourself and do the installation (configure - make -make install). In the process see if it has any specific options that you might have to put manualy for your camera. 
I have not hardy at the moment so I do not know about the available versions that the medubuntu repository gives you. Just do it for a test. I think that having tried all the things you say this would be a minor effort. 
Other than that is seems that it is a malfunction with the specific camera so in a future version this might be solved.

Regards!

Ah I see, thanks, I have never compiled  a program before other than by following step by step instructions.  

The medibuntu options give you an option that uses the default sound and Qt files. But then there is an option to use a Qt version that downloads with Skype and is only used by Skype. And there is an option that use the dedicated Qt option and a dedicated sound program. Presumably, aimed at avoiding compatibility issues with conflicting version numbers.

Certainly there does appear to be several problems listed in the Skype forum similar to mine, so it could well be a Skype software issue.  But I would have hoped that as the 9000 is the camera that Skype sell on their site and it is listed as being 100% Linux compatible on the Ubuntu site, that they would get it fixed fairly quickly.

Unfortunately, I will have to leave it for and go back to Windows to get some work done. I will have another go when I have some time to spare.

Thanks for the help.

Graham

---

