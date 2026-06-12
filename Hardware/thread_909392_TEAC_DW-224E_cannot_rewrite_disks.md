---
title: "TEAC DW-224E cannot rewrite disks"
date: 2008-09-03
forum: Hardware
---

### Post by davethewave83 on 2008-09-03
Hello!
I'm wondering if there is a way to get my TEAC DW-224E to rewrite in Ubuntu? I put a CD-RW in and it said probably the drive doesn't like the medium when I tried to erase it. Then I tried a DVD-RW and it doesn't even act like it sees a RW media in the drive it just says "Please insert a complete or appendable DVD +- R(W) medium" 

When I get properties on a CD-RW it says "Rewritable:  Yes" "Appendable: No" when I get properies on a DVD-RW it says "Rewritable: No" Appendable: No" and I know my drive is a RW drive, it says Rewritable on it's tray door (and used to work in windows) I've tried K3B and Brasero. 

Thanks!

---

### Post by RavanH on 2008-11-04
Hi Dave,

A month after you question, but maybe it is still useful for you (or others) so here goes.

Today I ran into a problem with a cd-r/w disk that was no longer recognized after a write failure. Inserting it resulted in nothing but 'no disk' being reported. I could not erase it with Brasero because of the fact that it was not even recognized as a disk, let alone a rewritable one...

After trying some other packages from Synaptic, I found the little program **cdrbq** to do the trick for me. After installing it ```
sudo apt-get install cdrbq
``` and running from terminal ```
cdrbq
``` and tinkering with some options (like setting disk location to /dev/cdrom1, selecting the very low 4x write speed and first choosing 'full erase' then a second time with 'fast erase') my rewritable came back to life again! :)

Good luck.
--ravan

---

