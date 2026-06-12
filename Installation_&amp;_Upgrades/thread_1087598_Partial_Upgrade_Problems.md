---
title: "Partial Upgrade Problems"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Colinho on 2009-03-05
Ok, so I decided that I would upgrade to 9.04 Alpha 5 from 8.10. I was downloading it through the package manager when my mum asked if she could check her email. So I did switch user and let her go on for a little while. The problem was a buggy screensaver that wouldn't wake forced me to Ctrl+Alt+Backspace (as a Linux newbie this was all I could do) and it didn't install. Upon my next session and run of the update manager, it said that not all updates could be installed and that I needed to run a partial upgrade. So I clicked the button, and a window popped up showing the update info (preparing, downloading, installing progress etc).

It goes through preparing upgrade and then the window disappears and nothing happens. Each time I open up update manager it tries to get me to do this again, so is there another way that I can run the partial update and upgrade to the 9.04 Alpha version through the terminal or something like that?

Thanks for the help ^^

Ps. Usually I try to fix things myself before going onto forums for help, but I have to go to bed soon so I thought that I could get a reply to see in the morning instead of spending some time doing trial and error. I'm sorry if the answer is really obvious (like downloading the full image) and I am wasting your time =\

---

### Post by zvacet on 2009-03-08
You can try with 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If you get any errors post it here.

---

### Post by Colinho on 2009-03-08
I ended up getting the partial upgrade to work, but my graphics card and screen drivers didn't work with 9.04, and I got a whole bunch of error messages. So in the end I decided to install 8.04 again.

So know I've learned an important Linux Lesson: When trying pre-release version, use a Virtual PC to test them.

Thanks for your reply though, perhaps I will try that if I need to in the future.

Cheers!

Btw how do I mark a thread as "solved"?

---

### Post by Neo_The_User on 2009-03-08
The solved feature has been removed. Btw about your drivers, 9.04 uses the cutting edge X11 and Xorg stuff (my favourite part of linux) so thats expected. It's Xorg server 1.6's fault that your drivers don't work. It's ok though. Just wait a bit and you'll live.

---

### Post by Colinho on 2009-03-08
Yea, sometimes I am too impatient to try a pre-release version when I should actually wait. Am I right in thinking that 9.04 is going to be released on April 23?

It'll be great ^^

---

