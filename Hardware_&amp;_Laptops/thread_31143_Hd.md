---
title: "Hd"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by sunpascal on 2005-05-02
Hi,

I'm new to linux and I had ubuntu running on an old pc. Now I wonder whether it would be possible to put the hard disk into another computer and run ubuntu on that copmputer without having to reinstall it. 

I even tried it, but X didn't start. 

Is there a way to make ubuntu re-detect the hard ware?

Thanks!
Pascal

---

### Post by Gandalf on 2005-05-02
[QUOTE=sunpascal]Hi,

I'm new to linux and I had ubuntu running on an old pc. Now I wonder whether it would be possible to put the hard disk into another computer and run ubuntu on that copmputer without having to reinstall it. 

I even tried it, but X didn't start. 

Is there a way to make ubuntu re-detect the hard ware?

Thanks!
Pascal[/QUOTE]
 try
```

sudo dpkg-reconfigure xserver-xfree86

```

NOTE: make a backup of your old /etc/X11/xorg.conf file just in case

---

### Post by TravisNewman on 2005-05-02
[QUOTE=Gandalf]try
```

sudo dpkg-reconfigure xserver-xfree86

```

NOTE: make a backup of your old /etc/X11/xorg.conf file just in case[/QUOTE]
 You may run into some other hardware problems other than X, but you might not. X is the big one though.

---

