---
title: "ext3 journalling error on resume"
date: 2008-09-21
forum: Hardware
---

### Post by DocFox on 2008-09-21
I have a dell D630 (Quadro NVS 135M graphics with the latest driver) with some serious trouble resuming from suspend-to-ram. i think i must have read/tried every solution here or in linuxquestions.org...

on resume, it is totally random if the computer recovers or not. weirdly i can switch terminals with ctl-alt-F but not reset X or use the rest of the keyboard. i need to do a hard reset.

when there is a crash, i get messages along the line of this:

```

Buffer I/O error on device sda7 logical block 6125626
journal commit i/o error
ext3_abort
ExT3-fs error (device sda7) ext3_journal_start_s3
Detected abnormal journal

```

also get for sda5 (my /), sda7 is /home

if anyone can get help me get some understanding of this problem and how to get around i will be very grateful. this problem is driving me nuts.

thanx

---

### Post by DocFox on 2008-09-25
bump

anyone feeling helpful tonight?[-o<

---

