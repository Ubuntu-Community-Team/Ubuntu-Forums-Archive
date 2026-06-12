---
title: "DVD+RW written in Windows recognized as &quot;Blank DVD+RW&quot;"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by Juissi on 2007-02-05
I have had this problem forever, from Hoary to Feisty. Self written DVD discs are not correctly recognized but movie-DVDs are. I recently got a DVD+RW disc written in Windows but Ubuntu thinks it's a "Blank DVD+RW". However, when I look at disc contents in Windows XP (running in Vmware server under Ubuntu) everything is fine. Burning DVDs can result in almost anything from a toaster to a fine-working disc.

DVD writer: Plextor 712 as primary master
HDD: Western Digital SATA
Motherboard: Asus A7V880

During the years only thing that has *not* changed in my configuration is the DVD burner that works perfectly in Windows. I am willing to replace if I could be sure that it would fix the problems. Any suggestions?

---

### Post by mikewhatever on 2007-02-05
This might be a dumb suggestion, but since I do not know the answer, I thought I'd try. Have you tried using DVD-R. They are supposed to be different, though I am not sure in what way. I do have some DVD-Rs burnt in Windows, and they work in Ubuntu too.

---

### Post by Juissi on 2007-02-06
I burned a couple of DVD's today to research this problem. It seems that when I burn a DVD+RW disc in Windows it has to be finalized. If multisession is in use, the disc is recognized as empty. With a DVD-RW disc this is not a problem. Come to think of this, this could be the reason to my burning problems also. The burner writes data succesfully but thinks the disc is empty until it is finalized.

I hope this behaviour is not by design. Any comments?

---

