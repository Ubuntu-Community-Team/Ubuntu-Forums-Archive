---
title: "djview problem"
date: 2005-12-21
forum: Installation &amp; Upgrades
---

### Post by lucascr on 2005-12-21
Dear all,

I have just installed all the djv* packages, except the djv*-dev one, but I'm not able to open any djvu file (both as firefox plugin or after saving the files on the desktop).
The error message I got is the following:
 
*** [1-11711] Failed to open 'page001.djvu': No such file or directory.
*** (ByteStream.cpp:728)
*** 'DJVU::GUTF8String DJVU::ByteStream::Stdio::init(const DJVU::GURL&, const char*)'

Any hint how to solve this problem? I did some mistakes?

Luca

---

### Post by gc1 on 2006-01-02
According to DjVuLibre it is necessary to"Copy or create a symbolic link to hsdejavu.so in your Mozilla plug-ins"
I wish I knew how to do that! I'm having the same trouble as above.
Graham

---

### Post by gc1 on 2006-01-25
I have now successfully installed djview. 
My problem was having an old version of it which I had downloaded before Ubuntu started to include it. (It failed to work after upgrading Ubuntu and I thought it was gone!)
 With 5.10 I got it with Synaptic Package Manager ONLY AFTER first uninstalling the older djview, as well as my new djview. In other words I had to start with a complete clearout, then Synaptic did a clean install for me.
Hope this helps someone.
Graham

---

