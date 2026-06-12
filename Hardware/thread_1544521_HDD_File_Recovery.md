---
title: "HDD File Recovery"
date: 2010-08-02
forum: Hardware
---

### Post by 3picide on 2010-08-02
Hi all, I have a friend's laptop that they are wanting me to look at. They said it never loaded. I tried it. It turns on, actually tries to boot Windows but then blue screens. I loaded a LiveCD and tried to mount the drive, but all I get are signs that the files are corrupted. I would like to get some files off of it before just wiping it (art work -- can't be reobtained, you know?). I just can't get it to mount. I know the hard drive isn't just dead (it does try to boot, which also means at least traces of the file system are there) and I know it's the hard drive (it boots fine off of a Live disc).

So, my main question is does anyone know of some recovery tools that may work? Even the mention of names would help (preferably Linux tools, but I can work with Windows). It seems at least feasible. I just don't know how.

I still have the laptop in my possession so I can answer any questions or give feedback from commands.

---

### Post by P4man on 2010-08-02
testdisk.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

To recover files, use [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") (part of testdisk suite). Runs on linux and windows and from some livecds. Its in the universe repos for ubuntu.

---

### Post by 3picide on 2010-08-02
> **P4man said:**
> testdisk.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

To recover files, use [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") (part of testdisk suite). Runs on linux and windows and from some livecds.

Thanks so much! This looks like exactly what I was looking for! I'll test it out and report back.

---

### Post by P4man on 2010-08-02
Some nice step by step guides on that site btw, like here:
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Also consider making a byte copy of the drive with dd, so you dont mess it up more than its already damaged. Testdisk will work on a dd image just as well.

---

### Post by 3picide on 2010-08-03
> **P4man said:**
> Some nice step by step guides on that site btw, like here:
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Also consider making a byte copy of the drive with dd, so you dont mess it up more than its already damaged. Testdisk will work on a dd image just as well.

Thanks again! I ran the photorec program on it (it took about 24 hours XD). I have a bunch of folders of data to sort through. It recovered about 10gb of stuff. I've looked through a few and it seems like mostly junk from her browser. Hopefully, her art is in there somewhere.

Now, I did try running dd on it just in case. However, it would only go about 400kb in before it just stopped. Not really sure what that's about.....

Anyway, thanks again! If this doesn't work, it just seems like there isn't much else to go on, so I'm considering it solved.

---

### Post by P4man on 2010-08-04
> **3picide said:**
> 
Now, I did try running dd on it just in case. However, it would only go about 400kb in before it just stopped. Not really sure what that's about.....

If its hardware failure, dd cant do miracles. It can make byte copies even of the most messed up partitions and filesystems, or no partitions or filesystems at all, but only if the drive still works; looks like a hardware failure caused all this.

Anyway, hope you recovered the stuff she needed.

---

### Post by 3picide on 2010-08-04
> **P4man said:**
> If its hardware failure, dd cant do miracles. It can make byte copies even of the most messed up partitions and filesystems, or no partitions or filesystems at all, but only if the drive still works; looks like a hardware failure caused all this.

Anyway, hope you recovered the stuff she needed.

I was thinking it was a hard drive failure, too. However, the file recovery program actually worked and I believe it went through all the sectors, so I don't understand why dd didn't work...... and I did get about 5 or so pictures that were worthwhile, but most of it was junk. Oh well. Thanks a bunch, anyway!

---

### Post by P4man on 2010-08-04
> **3picide said:**
> I was thinking it was a hard drive failure, too. However, the file recovery program actually worked and I believe it went through all the sectors, so I don't understand why dd didn't work......

I dont think dd has any logic that lets it skip a sector it cant read. It shouldnt either, at least not with the default switches. Photorec or testdisk obviously could try a few times and skip if it fails.

---

