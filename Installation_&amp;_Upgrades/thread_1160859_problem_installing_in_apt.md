---
title: "problem installing in apt"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by kiridude on 2009-05-16
Hi, I am trying to install qutecom. I have inserted the following into my /etc/apt/sources.list:

```

deb http://ppa.launchpad.net/cavedon/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/cavedon/ppa/ubuntu jaunty main
```

I have entered the key info from [here]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x282E4FAE542E7613E2DC4056C1FE1A7B426FF7FA&op=index") into software sources > authentication.

I ran "sudo apt-get update" and "sudo apt-get upgrade."

My problem begins here. Qutecom cannot be found by "sudo apt-get install qutecom" and is not listed in synaptic. I restarted my machine at this point just in case, but still no cigar.

Can someone point out what I have missed please.

---

### Post by kpkeerthi on 2009-05-16
I checked the [list of packages]("http://ppa.launchpad.net/cavedon/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages") provided by this PPA repository. qutecom is not listed there. You may want to contact the maintainer.

---

### Post by kiridude on 2009-05-16
Thanks kpkeerthi, you have solved the mystery.

I am abondoning qutecom as it is way more work than it should be. I actually want to pay to make calls to landlines, but now I discovered I can do that with Ekiga. For some reason I thought this was not possible. 

If I remove the repository entries and key for qutecom and run "apt-get autoremove" and "autoclean" will that get rid of the packages I downloaded from them?

Thanks

---

### Post by kpkeerthi on 2009-05-16
> **kiridude said:**
> 
If I remove the repository entries and key for qutecom and run "apt-get autoremove" and "autoclean" will that get rid of the packages I downloaded from them?

No it will not. If you installed any package from this PPA, you should remove them manually.

---

### Post by kpkeerthi on 2009-05-16
Oh yes. Just go ahead and remove this repository if you no longer need it.

---

### Post by kiridude on 2009-05-16
ok thanks

---

