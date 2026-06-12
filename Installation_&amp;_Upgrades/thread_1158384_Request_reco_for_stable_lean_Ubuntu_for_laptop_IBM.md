---
title: "Request reco for stable lean Ubuntu for laptop IBMT23, 1.0 GHz, 256 MB RAM"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by stemagic on 2009-05-13
Was running old version of Ubuntu (4, 5 releases old) on IBM T23 laptop, with 1.0 GHz processor, 256 MB ram, DVD drive etc., and all was fine.

Updating to 9.04 killed it. Now, HDD is reformatted, running Windows XP. 
Known good 9.04 live CD still will not work. get initramfs error. Same CD works on another laptop, a T60.

So, what is the best release of Ubuntu to run on this older T23? Also, I plan on using it mostly as my sound station => don't need too many apps on it.

So, are what are the latest recommended lean Ubuntu versions for older hardware, such this T23? Old releases? 

Or non-Ubuntu recommendations?

Thank you

---

### Post by dstew on 2009-05-13
Probably it is just the Live CD that is the problem. The Live CD operating system is less flexible that the full system. You could try to install 9.04 using the [Alternate Install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"). It installs the same Ubuntu desktop system, but it uses a text-based installer that might be more compatible with your laptop.

---

### Post by stemagic on 2009-05-18
Thank you, that was a good tip. The text based installer installed 9.04 and I can now dual boot into windows or Jaunty. However:

1. GUI based Update hangs; system says x files need to be updated with Y MB downloads. I click yes. the wheel keeps spinning, and system wont respond after a while.

2. Firefox won't open. Wheel keeps spinning

3. so started in safe mode with network and ran sudo apt-get update. That seemed to go thru some motions.

4. Go back to GUI and still have same problems with update stalling enytime is is opened (even via another package, such as rythbox asking to install codecs) and firefox will take for every when launched and then stall

5. FYI. Network connectivity via LAN works fine.

6. Is it puppy linux for this 1.0 GHz 256 MB T23? Is 9.04 beginning to forget older machines? Or do I need to debug a specific problem with my beloved T23?

Thank you

---

### Post by spcwingo on 2009-05-18
I have a desktop with similar specs.  All I did with it is an Ubuntu Hardy cli buildup.  It's not as hard as it sounds.  If you can sudo apt-get, you can do a cli buildup.  ;)

---

### Post by snowpine on 2009-05-18
If you are not satisfied with Ubuntu on your older hardware, give a lighter distro such as Crunchbang a whirl. Crunchbang is excellent as a "sound station" because it comes pre-installed with multimedia codecs and a good suite of multimedia apps.

---

### Post by dstew on 2009-05-19
In recovery mode, try```
sudo apt-get update
sudo apt-get upgrade
```The former command re-syncronizes apt-get with the repositories. The latter command is the one that gets your updated software. It is not a distribution upgrade, just an upgrade to the latest versions of your installed packages. See the [apt-get man page]("http://linux.die.net/man/8/apt-get").

Also, you may need to work on your /etc/apt/sources.list file. If it got corrupted somehow, it may not be pointing to active archives. Do the two commands above and see if you get any errors that would suggest this.

---

### Post by stemagic on 2009-05-19
Thank you for the useful suggestions, folks.

sudo apt-get update from CLI in recovery mode "hits" a bunch of sites. No errors.
sudo apt-get upgrade comes back with "all fine, no updates/upgrades needed"

Go back to GUI and same problem.

So I copied sources.list from my T60 (which runs 9.04 and works like a champ) into
etc/apt as su and changed permissions via chmod 777 for good measure.

Problems persist.

Suggestions?

Thank you

---

### Post by stemagic on 2009-05-19
as plan B, I'm now loading crunchbang, thanks to snowpine's reco.

Would still love to get 9.04 working, as a learning excercise if nothing else...

---

### Post by dstew on 2009-05-19
One other thing I might check is the System --> Administration --> Hardware Drivers menu item. Are there any third party drivers that might be installed? Overall, though, if the apt-get commands work OK, I am pretty much out of ideas.

---

### Post by stemagic on 2009-05-19
Reloaded 9.04 from alternate CD, wiped out and reformatted entire disk. Went fine.
Tried GUI update. Still stuck. Did update from terminal window and it went thru fine.
Now tried GUI update, it came back saying no updates needed. Now tried tried GUI synaptic (it did not work before), and it now works!

Thank you all. Don't know why or how, but problem solved!

Long live Ubuntu and the kind and knowledgable people who help us fix problems!

---

### Post by stemagic on 2009-05-19
One other thing. Firefox 3.xx seemd to be stalling, but it must have been the low mem, 356 MB, that made it crraaawwwllll.

Midori flies!

---

