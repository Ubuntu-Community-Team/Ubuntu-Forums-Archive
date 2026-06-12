---
title: "thinkfinger on 8.10..."
date: 2009-01-21
forum: Hardware
---

### Post by zander1013 on 2009-01-21
hi,

i am trying to install and use thinkfinger on my ibm t60 laptop. i have installed it using the synaptic package manager. now i am trying to use it. i was able to test with tf-tool --aquire and tf-tool --verify okay.

that seemed to work well. now i am trying to use it. so i added the line "auth<tab>sufficient<tab>pam_thinkfinger.so" to /etc/pam.d/common-auth. i used tabs because that is what they use in the common-auth file for white space between those columns (like fortran). they do not use the tabs in the docs.

so now i am trying to tf-tool --add-user $USERNAME but i get the error...

"Two output paths specified, but you may only specify one:
       --add-user
       $USERNAME"
(where $USERNAME is my username"
...

i am using ubuntu 8.10

some of the docs note that "User level driver support" compiled into your kernel or the "uinput" module loaded!". how can i test to see if this is true for me?

there seems to be allot of info on getting this fingerprint reader to work but none of it seem to be quite what i need to get going.

please advise.

---

### Post by chomski on 2009-01-22
Small world, I am having the same problem with a Dell Vostro _and_ an IBM x61, exactly the same issue on each of them as you're having.

Strange thing is that I had this working perfectly on 8.04 on the IBM x61, the "tf-tool --add-user" part was not an issue according to my old notes.
What has changed is that I'm using 8.10 (actually installed CrunchBang version 8.10), wondering if I should backtrack to hardy and see if that works.

Any help on this would be appreciated.

---

### Post by chomski on 2009-01-22
More investigation found this;
[https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/203973]("https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/203973")

So "--add-user" not used but still refered to in the man pages.
Still not working for me so I'm going to remove all thinkfinger stuff and start again.

---

### Post by chomski on 2009-01-22
Got it now, my problem was that I didn't use the sources from the howto. I removed all thinkfinger packages (--purge), then used the sources quoted;

deb [http://ppa.launchpad.net/jon-oberheide/ubuntu](http://ppa.launchpad.net/jon-oberheide/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/jon-oberheide/ubuntu](http://ppa.launchpad.net/jon-oberheide/ubuntu) intrepid main

Then ran apt-get upgrade, reinstalled libpam-thinkfinger and thinkfinger-tools, rebooted.

I ran tf-tool --acquire to capture the finger print, which writes to the user file, then tf-tool --verify.

Logged out and tried it ok.

Ignore the "--add-user" part, it's a red herring.

-----------EDIT-------------------------------
The howto I referred to is here;
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Ubuntu]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Ubuntu")

---

