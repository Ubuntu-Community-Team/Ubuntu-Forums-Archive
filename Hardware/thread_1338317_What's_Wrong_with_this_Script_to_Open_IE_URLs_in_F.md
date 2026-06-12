---
title: "What's Wrong with this Script to Open IE URLs in Firefox?"
date: 2009-11-26
forum: Hardware
---

### Post by OzzyFrank on 2009-11-26
Hi. A while back, I successfully used the guide for registering MHT web archives in this post: [http://ubuntuforums.org/showthread.php?p=3311005#post3311005](http://ubuntuforums.org/showthread.php?p=3311005#post3311005). The original purpose of the thread was on how to open **.url** internet shortcuts (what Internet Explorer puts on the desktop) in Firefox, so I gave it a go, expecting it to work as well as the other guide.

I've followed all the steps, but when trying to open an .url, Firefox will open, but instead of going to the web page, it gives me this error message:

**[COLOR="Blue"]Firefox doesn't know how to open this address, because the protocol (basehttp) isn't associated with any program.[/COLOR]**

You can read the whole guide via the link above, but here is the script:

[B][COLOR="DarkRed"]#!/usr/bin/perl

# Script to make Microsoft Windows Internet Shortcuts (*.url) work on Linux. 

# Oomingmak fixed version. This script now works properly.
# It no longer cuts off the last character of the URL.

# Open up the file
open(F,"<$ARGV[0]") or die "$0: Could not load Internet Shortcut file $ARGV[0]!\n";

# Find the URL
while($in = <F> and not $url) {
    chomp($in);
    if($in =~ m/\s*URL\s*\=\s*\S*\s*\015*/) {
        $url = $in;
    $url =~ s/\s*URL\s*\=\s*//; # Filter out the beginning stuff
    $url =~ s/\s*\015+//; # Filter out the nasty DOS carriage return!
        
        
    }
}

    system "firefox $url &";# or die "$0: Could not open $netscape\n"[/COLOR][/B]

If you can see something obvious, please leave suggestions to rectify this. Obviously I've assigned Firefox to open it, which it tries to, so the rest of it is beyond my understanding. Cheers. Frank

---

### Post by OzzyFrank on 2009-11-26
I managed to get an **.url** to open without that error, by editing its contents. Ideally, you shouldn't need to, and seems others who tried this had success without having to do so (at least on earlier versions of Ubuntu). This would be a pain for a Windows user with hundreds of **.url**s, but at least it works. Just open each **.url** file and remove the first 2 lines (as marked in red):

[COLOR="Red"][B][DEFAULT]
BASEURL=http://ubuntugenius.wordpress.com/[/COLOR]
[InternetShortcut]
URL=http://ubuntugenius.wordpress.com/
IDList=
IconFile=http://www.gravatar.com/blavatar/b040b12c9e739ace052197f85996bd27?s=16&d=http://s.wordpress.com/favicon.ico
IconIndex=1
[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,2[/B]

If someone could supply a command that removes the first 2 lines of all files with the **.url** extension, please post it here.

PS: I still have no idea why people save **.url** files in My Documents and on the desktop... I mean, haven't you guys heard of the Favorites menu (Bookmarks in every other browser)? [I'm doing all this for someone who never listened to me regarding this, but now plans to bookmark each of the sites the .urls open]

---

### Post by vwood on 2013-03-15
The regexp that matches the "URL=" will skip the "BASEURL=" if you anchor the URL with ^URL
```
if($in =~ m/\s*^URL\s*\=\s*\S*\s*\015*/) {
```

---

### Post by lykwydchykyn on 2013-03-15
> **OzzyFrank said:**
> 
If someone could supply a command that removes the first 2 lines of all files with the **.url** extension, please post it here.


```

find ./ -iname "*.url" -exec tail --lines=$[ $(wc -l <{}) - 2 ] {} \;

```

---

### Post by QIII on 2013-03-15
Back to sleep.

---

