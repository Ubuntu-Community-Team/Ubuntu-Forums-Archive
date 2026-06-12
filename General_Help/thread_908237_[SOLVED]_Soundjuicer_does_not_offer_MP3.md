---
title: "[SOLVED] Soundjuicer does not offer MP3"
date: 2008-09-02
forum: General Help
---

### Post by johann_p on 2008-09-02
In the preferences, Soundjuicer does not offer MP3 as a possible output format. However, Edit Profiles ... does show a "CD Quality, MP3" profile. This profile is not available in the selection menu for "Output Format" though.

Why? And how can I make Soundjuicer produce MP3 output?

---

### Post by Vivaldi Gloria on 2008-09-02
I guess you don't have lame mp3 encoder. Start

system menu > admin > synaptic

Also enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh. 

Now you can search and install whatever you want in synaptic. For example search and install

```
ubuntu-restricted-extras
```

which contains lame, java, codecs, and other goodies. Or just install lame.

---

### Post by kpkeerthi on 2008-09-02
[https://help.ubuntu.com/community/CDRipping#Installing%20Additional%20Audio%20Formats](https://help.ubuntu.com/community/CDRipping#Installing%20Additional%20Audio%20Formats)

---

### Post by johann_p on 2008-09-02
Excellent - thank you for your help!

---

