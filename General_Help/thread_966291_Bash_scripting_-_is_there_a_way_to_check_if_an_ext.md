---
title: "Bash scripting - is there a way to check if an extraction has failed?"
date: 2008-11-01
forum: General Help
---

### Post by gnuvistawouldbecool on 2008-11-01
I've made a simple shell script to download and extract the latest Firefox 3.1 nightly builds, and have made it download the tarball, followed by extracting it, then running the latest firefox build (mostly because I like having some cutting edge programs on my computer).  This morning, it came across an error that output this:

```

(up to this point extraction was normal)
firefox/dictionaries/en-US.dic
firefox/libxul.so

bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
```

My script then went on as normal, and tried to run Firefox, but it failed.  On a second attempt it ran perfectly fine.

So what I'm wondering is, how can I make it stop and exit if the decompression comes across an error?

The script, so far, looks like this:

```
wget http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/firefox-3.1b2pre.en-US.linux-i686.tar.bz2
echo "tarball downloaded, extracting..."
tar -vxf firefox-3.1b2pre.en-US.linux-i686.tar.bz2
echo "Tarball extracted, removing"
rm firefox-3.1b2pre.en-US.linux-i686.tar.bz2
echo "Starting Firefox..."
cd ~/firefox/
./firefox
```

---

### Post by happyhamster on 2008-11-01
I'm no expert on bash (at all), but you could try something like this:

```

if [ `tar -vxf firefox-3.1b2pre.en-US.linux-i686.tar.bz2` ]
then
    echo "Tarball extracted, removing"
    rm firefox-3.1b2pre.en-US.linux-i686.tar.bz2
    echo "Starting Firefox..."
    cd ~/firefox/
    ./firefox
fi

```

It looks a bit like C code this way :) Anyway, good luck, and keep us informed.



See: [http://steve-parker.org/sh/external.shtml](http://steve-parker.org/sh/external.shtml)

---

### Post by geirha on 2008-11-01
Quite certain you'll get a syntax error with that if, but it was close to the correct way:
```

if tar -vxf firefox-3.1b2pre.en-US.linux-i686.tar.bz2; then
   echo "Succeeded."
   rm ...
else
   echo "Failed to extract ..."
fi

```

---

### Post by gnuvistawouldbecool on 2008-11-02
Ok, thanks, I'll try that.  I was expecting something more difficult looking than that.

Edit:  Thanks, it worked.  Well, it did when the if statement returned positive, at least.

---

