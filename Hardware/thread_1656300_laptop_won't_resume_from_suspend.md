---
title: "laptop won't resume from suspend"
date: 2010-12-30
forum: Hardware
---

### Post by catlover2 on 2010-12-30
Hello,

I have a Toshiba Satellite M30X laptop, and when suspended,
it will not resume, just a nonblinking cursor.

I understand this has something to do with my Atheros AR5001X+ wireless card,
but have no idea what to do about it.


Thanks,

Catlover

---

### Post by catlover2 on 2011-01-05
(bracing myself...) [COLOR=Red]BUMP![/COLOR]

---

### Post by jeduffey on 2011-06-09
Are other people having this problem?
My Toshiba Portege M400 has been very happily running 10.10 with perfect suspend resume results for months. Then I upgrade to 11.04 Natty and it fails completely. Suspend works, but resume fails, which makes suspend completely worthless. I get a black screen with a blinking white line cursor. So maybe the resume is ok, but the video fails? This situation is rather ridiculous. It seems the suspend / resume fail is an every other update issue with Ubuntu. This should be a once and done fix, don't break it again kind of deal.

Bummed.

---

### Post by jeduffey on 2011-06-09
I found this info
[http://techie-buzz.com/foss/ubuntu-user-mode-x-server.html](http://techie-buzz.com/foss/ubuntu-user-mode-x-server.html)
Looks like that's what is broken.

---

### Post by jeduffey on 2011-06-09
Here is some more info.
TuxOnIce - I am trying it.
[http://askubuntu.com/questions/45104/hibernation-does-not-work-in-11-04-used-to-work-in-10-10-but-suspen-resume-work](http://askubuntu.com/questions/45104/hibernation-does-not-work-in-11-04-used-to-work-in-10-10-but-suspen-resume-work)

sudo add-apt-repository ppa:tuxonice/ppa
sudo apt-get update
sudo apt-get install tuxonice-userui linux-generic-tuxonice linux-headers-generic-tuxonice

I'll let you know.

---

### Post by jeduffey on 2011-06-09
Good news, it worked.

Bad news, does not work with PAE RAM extension, so I lost access to the top of my 4GB.

---

