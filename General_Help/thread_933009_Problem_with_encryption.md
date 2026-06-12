---
title: "Problem with encryption"
date: 2008-09-29
forum: General Help
---

### Post by yoyo20007 on 2008-09-29
My old Laptop died and I bought an EEE1000h. I was using Suse 10.0 and wanted to switch a long time to Ubuntu/Kubuntu. I realize now that the grass is always greener on the other side.

My current problem:

I have two external harddrives.

1st AES256 encryption, passphrase >20
2nd TWOFISH encryption, passphrase <20

I don't manage to mount any of them via losetup

modprobe aes or aes256 gives an error (error inserting padlock aes)
Hence can't mount

modprobe twofish seems OK

I can't mount the other with twofish  because I used a keyphrase with less than 20 characters.

So there is no way to acccess any of this encrypted hdd from Ubuntu?

---

