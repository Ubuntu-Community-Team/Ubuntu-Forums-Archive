---
title: "Does the iPod 5.0.1 work yet? Is there a fix for the checksum problem on the horizon?"
date: 2012-09-02
forum: Hardware
---

### Post by spaceshipguy on 2012-09-02
I've had an iPod for half a year now. It came with OS 5.0.1 - the one that isn't working with Ubuntu right now. Nothing, (not Banshee, not Clementine, nothing), will transfer music to it.

OS 4 works for music transfer, apparently, but I don't fancy hacking the iPod to revert back to an older OS.
I also have a Windows virtual machine, but I would prefer to be able to use a native Ubuntu music application, rather than run Windows and download iTunes (it's just a nasty silver monster). 
And I also have DONUT on the iPod (a free music player from the Apple app store) and I can drag music to the device for DONUT to play, but I would prefer to use the normal iPod player.

So I have lots of ways to get music on to the device, but I would prefer to drag and drop, or sync with Clementine.

I was wondering if anyone had heard of any progress in cracking Apples new database checksum shenanigans? Is this on the horizon, or still a few months away?

---

### Post by spaceshipguy on 2012-09-09
Update,

Donut isn't a great player, and Windows 7 refuses to recognize the iPod without non-trivial intervention. (I must admit I was amazed that the iPod is so flaky with Windows). 

So my options now are hack the iPod and revert to an earlier OS, or buy and virtualize an Apple operating system. 

Grrr!

Unless someone has iPod OS 5.0.1 talking to their Ubuntu setup?

---

### Post by dandnsmith on 2012-09-09
"Donut isn't a great player, and Windows 7 refuses to recognize the iPod without non-trivial intervention. (I must admit I was amazed that the iPod is so flaky with Windows). "
I don't know why you'd be so surprised - Apple has always tried to maintain a closed shop - even worse than M'soft in its studious ignoring of things-not-Windows, and resolute refusal to publish the interfaces

---

### Post by spaceshipguy on 2012-09-11
[http://www.youtube.com/watch?v=gFmNG2k5ENw](http://www.youtube.com/watch?v=gFmNG2k5ENw)

It looks like I could just put Ubuntu on the iPhone. Although if I can't get the iPhone to work with Windows 7, perhaps I'm not the one to be trying to do this.

---

### Post by spaceshipguy on 2012-09-12
Progress
I jailbroke the iPhone with absinthe-linux-2.0.4 It was a pleasure - just worked. I think you have to have the ipod connected to the internet via an ad-hoc connection though.

Then I downloaded MyFile from Cydia - the new software centre that appeared on my iPod.

Then I generated a hash info file [at this site]("http://ihash.marcansoft.com/"), following instructoions within MyFile.

I can now move a song from the ipod into Rhythmbox (but perhaps I could do that all along?) Still can't move a file to the iPod via drag and drop - the functionality I most desire.

[This thread]("http://ubuntuforums.org/showthread.php?t=1908672&page=3") tells that pwntunes works, but it costs money.
I'm going to soldier on trying to get Rhythmbox to work. I feel like I'm closer.

---

### Post by spaceshipguy on 2012-09-16
The iPod is now working with Ubuntu (sort of). I can drag and drop any file onto the pod, although I can't access the whole file tree from the computer. I can from the phone itself though with MyFile.

I've installed OPlayer Lite and CloudReaders so I can drag and drop music and comic books to my iPod, and that's given me the functunality I needed.

I just gave up trying to get the default music app to sync - I prefer dragging and dropping files anyway.

Will update first post with my &#8216;solution&#8217;.

-----

Oops can't edit first post, so solution here then.

The only solution I found (it has been mentioned a couple of times in the forums before) was to install specific apps that deal with the filetypes you need to access. 
Once the app is installed you should have a folder that you can add the files to in the &#8216;documents&#8217; window that opens along with the iPod window in Nautilus. 

I installed OPlayer Lite and CloudReaders so I can drag and drop music and comic books to my iPod, and that's given me the functionality I needed.

(Optional 1.. Jailbreak the iPod.
This can be done with absinthe-linux-2.0.4 (it's free). 
This ran fine for me on 64-bit Pangolin, jailbreaking iOS 5.0.1 - it was a pleasure - just worked. I think you have to have the iPod connected to the Internet via an ad-hoc connection though.

Then download MyFile from Cydia - the new software centre that appears on the jailbroken iPod (it's free).

Now you have access to your device's file tree. Just like with a rooted Android device.

(Optional 2.. if you want to try and get syncing to work (I gave up) -- Then generate a hash info file at this site [http://ihash.marcansoft.com/](http://ihash.marcansoft.com/) following instructions within MyFile. There is a free app in the store to display your devices handy 40 character UUID, which is required to generate the file.)

---

