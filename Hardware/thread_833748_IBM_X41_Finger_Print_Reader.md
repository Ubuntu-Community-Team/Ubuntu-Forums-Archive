---
title: "IBM X41 Finger Print Reader"
date: 2008-06-18
forum: Hardware
---

### Post by shooterjames on 2008-06-18
HI,

Can anyone help with the config of my fingerprint reader? I just installed Ubuntu on my x41 and i would like to get it working if possible [Lazy really can't be bothered to keep entering my password].

I have exactly zilch experience of Linux so dumb proof help would be much appreciated.

thanks, Rock on!:guitar:

---

### Post by wenuswilson on 2008-06-19
Well, for starters... 

[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Hardy](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Hardy)

You said 8.04 Hardy Heron so...

Open a terminal and type in

> sudo apt-get install thinkfinger-tools libpam-thinkfinger 

When that's done type in

> sudo /usr/lib/pam-thinkfinger/pam-thinkfinger-enable 

Have it get your fingerprint

> tf-tool --acquire

Do it 3 successful times.

Should be all you need.

---

### Post by shooterjames on 2008-06-19
Cheers, somthing has gone wrong. The install went ok and I ran the --aquire three times.

When i ran the tf-tools --verify it said that the communication with the fingureprint reader failed.

I rebooted and after entering my username i got the password or swipe finger prompt, i swiped my fingure and it loops back to username i cant override with my password also i seem to be stuck in this loop between username and password.

oops

---

### Post by shooterjames on 2008-06-19
additional i tried holding esc down and it will allow a text entry on the password but it only gives what seems like a nano second to type anything in before it jumps back to the username prompt.

argh...fresh install on the horizon i think.

[Note to anyone trying this make sure your reader actually works...doh!]

---

