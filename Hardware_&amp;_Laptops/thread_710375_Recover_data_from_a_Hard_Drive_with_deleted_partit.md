---
title: "Recover data from a Hard Drive with deleted partitions"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by tenjin1 on 2008-02-28
I have a ext3 hard drive seperate from my ubuntu installation with deleted patitons and has important files on it I need to recover. I have tried partimage, rsync, ddrescue, etc with no luck because these programs seem to require the partion already there and errors out with different I/O errors, which seem common errors for these programs when no partitons are found.

Is there any other linux programs that will recover files from deleted partitions? I would like to find a solution before I shell out allot of $$$ to some recovery company.

EDIT: Also like to add, no data has been written to the hard drive since the partiton was deleted.

---

### Post by aysiu on 2008-02-28
Run a live CD and install *testdisk*.

Then run the command ```
photorec
```

---

### Post by IcarusR on 2008-02-28
Hi

Checkout these links, they might help you... the first Ubuntu Data Recovery documentation, the second is aTest Disk  Howto .

[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

[http://www.users.bigpond.net.au/hermanzone/p21.html]("http://www.users.bigpond.net.au/hermanzone/p21.html")

Good luck

---

### Post by az on 2008-02-28
> **tenjin1 said:**
> I have a ext3 hard drive seperate from my ubuntu installation with deleted patitons and has important files on it I need to recover. I have tried partimage, rsync, ddrescue, etc with no luck because these programs seem to require the partion already there and errors out with different I/O errors, which seem common errors for these programs when no partitons are found.

Is there any other linux programs that will recover files from deleted partitions? I would like to find a solution before I shell out allot of $$$ to some recovery company.

EDIT: Also like to add, no data has been written to the hard drive since the partiton was deleted.

If the partition is just deleted, try to add it back to the partition table using testdisk or parted (parted has a rescue function which will scan your drive for lost partitions).

If that fails, then data-carve the files out using photorec.  You don't need the partition to be there for photorec to find files.  Foremost is also effective at carving out files.  See the DataRecovery page mentioned previously.

---

### Post by tenjin1 on 2008-02-28
Thanks everyone for all the replies.

I will install the Hard Drive back into my PC, since it is a seperate drive I had.  With that being said, since it's a seperate Hard Drive do I still have to use a LiveCD?

Also, foremost seems really good, but have already tried and errors out. Will defintely try TestDisk with photorec, that seems like the ticket! :)

Will post back when I try it out.

---

### Post by az on 2008-02-29
What do you mean by error out?  If you cannot properly read the drive, then it is not simple a case of a lost/deleted partition, but a faulty drive.

If the drive is faulty, then stop playing around with it and image it.

Then try to recover the partition/files from the image.  Again, see the DataRecovery wiki page.

---

### Post by tenjin1 on 2008-02-29
Ok, Photorec is the only thing that seems to work out of all of them (didn't try to make image with Partimage). It is backing up my data right now.
Thanks aysiu and others for pointing me to Testdisk with Photorec!

---

