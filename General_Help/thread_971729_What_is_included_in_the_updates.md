---
title: "What is included in the updates"
date: 2008-11-05
forum: General Help
---

### Post by sesquipedalianman on 2008-11-05
So this morning in my Kubuntu 8.10 install I was prompted to install a bunch of updates - kernel, kde, plasma, other stuff.  I saw that the kernel update is due to some vulnerabilities, but I can't seem to find what is included in the other updates.  I'd like to know if they are bug fixes, and if so what bugs they fix?  If they are improvements, what do they improve?  Are their new features being added?  Can anyone point me to where I would find this information?  Thanks.

---

### Post by geirha on 2008-11-05
I don't know what program is used in kubuntu to install updates, but in ubuntu, with the update-manager it uses, you can click on "description" to see a description of what each update fixes. Sometimes it's unable to download these descriptions for whatever reason. If that happens, I just close the update-manager and wait a while before I try installing the updates again. I too want to know what the updates fixes.

After the updates are installed, you can also see what they did. For example, to see the changes done for the kde package, you can type in a terminal ```
aptitude changelog kde
```

---

### Post by sesquipedalianman on 2008-11-05
I'll check for the details next time.  I guess I had been hoping for something like an rss feed with that type of details, the changelog helps as well.  Thanks.

---

### Post by sesquipedalianman on 2008-11-07
Well that was disapointing.  Adept updater gives me a link stating more which on each of the last 8-10 updates has pointed to the useful link "foo".  I guess I'll have to manually go through the changelog post deployemnet.  :confused:

---

