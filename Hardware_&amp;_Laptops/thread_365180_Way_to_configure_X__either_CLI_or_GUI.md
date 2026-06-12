---
title: "Way to configure X?  either CLI or GUI?"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by linuxaz on 2007-02-19
Hello,
I'm testing Feisty herd 3 here, but upgraded to the later via repos last night.  I don't think my question is limited to Feisty, (yes I now testing only) so i'm posting it here.

I've been using Linux about 5 years now, currently I'm on SuSE 10.2, but was intrigued by the sheer amount of software for Ubuntu, so I'm trying it.

Now for the question, I installed the Nvidia driver via synaptics but (I know this is dumb) I didn't make a copy of my xorg.conf file......  Well, as you can guess, the install didn't work, and dropped me back to text mode.    So, using VI, I edited the xorg.conf file to say "nv" instead of nvidia.  it was a NOGO, and x still didn't start.  This is when I started searching for a CLI or text mode way (yast2 equiv) to reconfigure X.  I have not found what Ubuntu has in this regard yet.  Can anyone point me in the right direction?

Later, after re-installing the OS, I found that the driver is still stuck on vesa!  Is this a bug, that Ubuntu's hardware detection did not pick up my nvidia 5200 card properly? 

I appreciate any help.

Regards,

linuxaz

---

### Post by erkki70 on 2007-02-19
Hi,
You could try:

```
sudo dpkg-reconfigure xserver-xorg
```

You'll be prompted questions to answer and you should get back on tracks this way I guess...
Hope this helps...
Cheers,

---

### Post by linuxaz on 2007-02-19
Erkki70,
I have seen this listed.  However, when I tried, it complained that it was not an installable package.  If it happens again, I'll give it a go.

Thanks,
linuxaz

---

