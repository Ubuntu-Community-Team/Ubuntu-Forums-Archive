---
title: "Recommendation for Tablet Laptop"
date: 2010-02-15
forum: Hardware
---

### Post by jaem on 2010-02-15
I'm a university student in computer engineering, and I'm looking into getting a tablet laptop for note-taking, as a lot of my lecture notes are diagram-intensive, or are provided as skeleton notes ahead of time by a prof who then fills them in on his/her own tablet.  The catch is that I'm getting it (if I do at all) through a government program, and as such, my options are limited to whatever they find in a certain price range from whichever manufacturers they do business with.  What those two parameters are, I have no idea, except that they usually buy Dell.  I've been unable to find much concrete information on the current state of support for any current-generation tablets, though.  I use Linux in general, but I don't mind dual-booting Windows for a while, or suffering through issues while waiting for hardware support to catch up; however, I don't want to ask for a piece of hardware that isn't likely to work any time soon.

What I'm hoping for is someone who has run *buntu or Arch (or anything other distro, for that matter) on a recent tablet from a major manufacturer to give me a confirmation that it runs, and any additional info that you think might be helpful (e.g. citations, other posts, links to workarounds, if you have them handy, whatever).  The Dell Latitude XT2 is one I'm particularly interested in.
For the record, I'm not sure which distribution I'd end up choosing for it, but Kubuntu is high on the list, and I thought my chances of getting a timely answer here better than some other forums.

Thanks a lot

---

### Post by jaem on 2010-02-15
I'm sorry... It's been a while since I used this forum, and I forgot that this wasn't really the section to post under.  Could a moderator please move it somewhere more appropriate, and accept my apologies.  Thanks

---

### Post by Favux on 2010-02-15
Hi jaem,

The Dell XT2 is kind of pricey.  And it has a N-trig digitizer.  Since N-trig doesn't support linux we rely on folks like Rafi Rubin and Ayuthia to get it working.  Rafi has a new hid-ntrig.ko we have high hopes for.  See:  [http://ubuntuforums.org/showpost.php?p=7863677&postcount=1](http://ubuntuforums.org/showpost.php?p=7863677&postcount=1)

Unless the price has come down, for a similar amount I think a Thinkpad X200t might be a better buy.  Or for a less expensive model with alleged good battery life the new HP TM2.  Both of those have Wacom digitizers and should be supported "out of the box" with Lucid, due out in April.

---

### Post by jaem on 2010-02-16
Thanks, Favux!  I knew N-Trigs were nasty, but I didn't know support was quite that experimental.  Probably not the best choice, then.  Out of curiousity, though, would/will the experimental driver support multitouch at the driver level? (I know it isn't supported higher up in the stack yet)
I'll look at the Thinkpad tonight, although I don't know if I'l get much choice in the end.  HP I try to stay away from, due to bad experiences with tech support, but thanks for mentioning it.

---

### Post by Favux on 2010-02-16
Multi-touch is one of the aims of Rafi's new kernel driver hid-ntrig.ko.  He has it working on evdev he says.  And Ayuthia has been working on a specific Xserver n-trig driver that supports multi-touch along with his modifications of hid-ntrig.ko.  He says he has multi-touch.  He's also looking into udev and some multi-touch achieved by others.  So n-trig might be in business soon, with luck.

---

### Post by jaem on 2010-02-22
Thanks for the info.
However, the main thing I was hoping to find out with this thread was whether the laptop in general is usable, or usable enough to get by.  As I said, I'm probably not going to have very many options, so if tablet functionality isn't 100% for a few months, that's no big deal. However, I've had all manner of fun with troublesome laptops before (*cough* Broadcom/ATI), and I was hoping someone who'd tried the XT2 personally could give me some general feedback.  From the spec listing on Dell's site, it looks mostly okay, with the possible exception of Dell's rebranded (?) wireless cards, which I've heard bad things about, and the Intel GMA 4500MHD, which seems impossible to find any conclusive information about.  (I've seen countless posts on these forums about it, so if there *is* anything conclusive (or at least, up-to-date), a link will do - I don't want to trouble anyone to explain it all)

Thanks again

UPDATE: I it turned out that it was an option between an HP tablet or a (non-tablet) Dell Latitude E6500, and I ended up going with the latter due to my aversion to HP.  I appreciate the suggestions and pointers, though

---

