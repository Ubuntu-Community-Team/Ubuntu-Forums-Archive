---
title: "Should I worry about SSD when I am not using TRIM in ubuntu 13.10?"
date: 2014-03-28
forum: Hardware
---

### Post by pavelexpertov on 2014-03-28
Hello, I have received a new laptop, ASUS N56VB with intel i7 and 8GB RAM, and I bought a SSD, which is Samsung 840 evo 500GB. I installed Windows 7 and Ubuntu 13.10 on the SSD and my machine is fast as 'horse on steroids', since my spec is asuited to get the full performance out of SSD. I read an article about TRIM one day and I know that windows 7 is supposed to do TRIM automatically. However, I am a bit worried that ubuntu can affect its own partition if I leave it untrimmed for a long time. So my question is: Does ssd damage itself if I leave the partition untrimmed for a while before 14.04 gets released? I read that it's 'theoretically' possible to fix untrimmed places and does it mean I would have to delete the partition and then extend windows 7's partition in order to trim it? Thanks.

PS. Here is the article that I read:
[http://www.howtogeek.com/170752/htg-explains-should-you-use-an-ssd-optimization-utility/](http://www.howtogeek.com/170752/htg-explains-should-you-use-an-ssd-optimization-utility/)

---

### Post by Kris_Spencer on 2014-03-28
It's a really good idea to use trim. It's not that your SSD will get  damaged, it's that you need to free the no longer used blocks. You do  not have to have Windows to it for you, though. You can do one of three  things:

1. Mount your partitions with the discard option. Edit /etc/fstab to do this. It should look something like this: 

# / was on /dev/sda3 during installation
UUID=f2cd20ad-00ae-4c01-a296-cba7659464a5         /                       ext4    defaults,discard        0 1

2. You can run the command yourself occationally. Just use: sudo fstrim -v /

3. You can set up a cron daemon to do number two for you every so often.

---

### Post by pavelexpertov on 2014-03-28
Thanks, what is cron daemon? Is it like a script that runs at certain times?

---

### Post by Kris_Spencer on 2014-03-28
Yes. The cron daemon runs repeated tasks at the times you specify. So basicly, you can tell you computer to run the trim command at 1AM every Friday or whatevery schedule you want. BUT the computer MUST be on during the times listed. If it's not, it will just ignore the fact that it missed it.

---

### Post by coldraven on 2014-03-29
> **Kris_Spencer said:**
> Yes. The cron daemon runs repeated tasks at the times you specify. So basicly, you can tell you computer to run the trim command at 1AM every Friday or whatevery schedule you want. BUT the computer MUST be on during the times listed. If it's not, it will just ignore the fact that it missed it.

So you could use anacron instead. 
```
man anacron
```

---

### Post by pavelexpertov on 2014-03-29
Thanks guys!!!!!!!!

---

