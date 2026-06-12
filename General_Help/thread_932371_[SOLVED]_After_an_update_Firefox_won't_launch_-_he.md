---
title: "[SOLVED] After an update Firefox won't launch - help!"
date: 2008-09-28
forum: General Help
---

### Post by staib on 2008-09-28
Hi all,

I saw in a update that Firefox was being updated to 3.0.3 (I think) - but it now won't launch. I have used synaptic to remove and add back again but no joy. If I click on Applications > Internet > Firefox I see the starting Firefox thing at the bottom for 20 secs or so then it closes and nothing.  Any help appreciated to sort this one.   
Cheers,  Nick
(Ubuntu 8.10)

---

### Post by mikewhatever on 2008-09-28
Try launching it from terminal by typing firefox and post the terminal output here.

---

### Post by Dougie187 on 2008-09-28
You might have to clear out your firefox settings.

If you want to give this a shot, just go to a terminal and type
```
mv ~/.mozilla ~/.mozilla.bak
```

If this works, you will probably have to redo all of your preferences, but thats not a huge pain. If you need any file from your old firefox they would be in the ~/.mozilla.bak directory.

To move stuff back (in the event it doesn't work) you can just type
```
mv ~/.mozilla.bak ~/.mozilla
```

---

### Post by staib on 2008-09-28
Thanks for those suggestions.  They are appreciated, but did not get Firefox back up.

Mike: launching from a terminal, produced: "The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0" - as I mentioned I had already installed it from Synaptic (and it was there before it stopped working!

Dougie187: I tried those commands but it makes no difference...

Any more ideas?!   Cheers

PS When I check the launch command on the menu it is "firefox-3.0 %u" - is this correct?

---

### Post by leith98b on 2008-09-28
I also have the same issue.  Typing 'firefox' at the command line returns a "Segmentation Fault"

Running an strace on firefox has the following on the end...

stat64("/usr/lib/xulrunner-1.9.0.3/components/websrvcs.xpt", {st_mode=S_IFREG|0644, st_size=14742, ...}) = 0
open("/usr/lib/xulrunner-1.9.0.3/components/websrvcs.xpt", O_RDONLY|O_LARGEFILE) = 14
read(14, "XPCOM\nTypeLib\r\n\32\1\2\0Q\0\0009\226\0\0\0\"\0\0\10"..., 14742) = 14742
brk(0x8137000)                          = 0x8137000
close(14)                               = 0
stat64("/usr/lib/xulrunner-1.9.0.3/components/pipnss.xpt", {st_mode=S_IFREG|0644, st_size=12844, ...}) = 0
open("/usr/lib/xulrunner-1.9.0.3/components/pipnss.xpt", O_RDONLY|O_LARGEFILE) = 14
read(14, "XPCOM\nTypeLib\r\n\32\1\2\0B\0\0002,\0\0\0\"\0\0\7Y"..., 12844) = 12844
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++


Does that help anybody?

---

### Post by staib on 2008-09-28
Not sure this is the same issue, Leith - although the symptoms sound the same. I certainly don't get any reference about a segmentation fault. Might be worth starting a different thread (but keeping an eye on this one) other wise it could get confusing. Cheers and good luck.

---

### Post by leith98b on 2008-09-28
sounds good, I'll start another one about Firefox segfaulting.

---

### Post by Jeroensum on 2008-09-28
@ leith98b
Seems your problem is in a Addon firefox is trying to run.
Try to start firefox with the  -safe-mode option.

---

### Post by leith98b on 2008-09-28
Thanks for the reply - I just tried that, though, and the result is the same.

---

### Post by staib on 2008-09-28
Just been digging around and I have found 'Firefox 3' in a folder.

It's in usr > lib > firefox-3.0.3 and I can launch the firefox icon in there directly.  It goes into a new user (do you want to import your bookmarks) routine...

How do I get the normal Applications > Internet > Firefox menu to 'see' it and launch it.

---

### Post by staib on 2008-09-28
OK - I think this is now solved - I just created a new menu item (pretty intuitive) - not sure if it will survive the next Firefox update, but it's good enough for now. Thanks all who helped, and good luck to those still seeking help... :)

---

