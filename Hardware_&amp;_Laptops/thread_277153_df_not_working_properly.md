---
title: "df not working properly"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by dinamic on 2006-10-14
> dx@dx-laptop:/media/x$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda7             4.5G  3.0G  1.3G  71% /
varrun                236M   88K  236M   1% /var/run
varlock               236M  4.0K  236M   1% /var/lock
udev                  236M  100K  236M   1% /dev
devshm                236M     0  236M   0% /dev/shm
lrm                   236M   18M  218M   8% /lib/modules/2.6.15-27-k7/volatile
/dev/hda1             9.8G  9.3G  522M  95% /media/hda1
/dev/hda5              20G   20G  209M  99% /media/hda5
/dev/hda6             2.9G  2.7G     0 100% /media/x
dx@dx-laptop:/media/x$ du --max-depth 1 -h
12K     ./lost+found
823K    ./Docs
2.0G    ./tmp
1.0K    ./Movies
19M     ./Music
11M     ./Pictures
64K     ./etc
2.0G    .


Can someone explain to me what is this bug about ?
My /media/x/ was full, I have deleted some media files.. and now it is 2GB, but 'df -h' displays 2.7GB. What's wrong?
I post this problem in this category, because it occures my notebook - ACER 3002NLC.

---

### Post by meng on 2006-10-14
Just checking - you deleted AND emptied the Trash, I assume?

---

### Post by dinamic on 2006-10-14
I have removed them with Shift+Delete, that way they are not going to Trash bin.
Anyway, I do checked the Trash bin and they were not there.
By the way, did I saw what I have in my 1st post ?
There is a "du --max-depth 1 -h" executed, and it clearly says that the space is "2GB", but "df -h" says 2.7GB.

---

### Post by meng on 2006-10-14
Yes thanks for pointing it out, but you executed the command with maximum depth of 1. I'm not a mind-reader, how would I know whether or not you have subdirectories containing other files? You didn't specify so in your original post OR your second post. I know if I executed the same command on my media folder, it wouldn't report the total accurately because I have quite a deep folder tree/structure.

You know I really don't mean to offend you by asking such a simple question, it's just that there are quite a lot of new users around here and even more experienced users can overlook simple things sometimes.

I'll be the first to admit that my Linux knowledge is limited, and I'm sorry if I don't know enough to help you with your problem.

---

### Post by dinamic on 2006-10-14
meng, no offence man.. but I have pointed this out in the first post of mine :)
Here is the output of the "df -h":
> dx@dx-laptop:/media/x$ du --max-depth 1 -h
12K ./lost+found
823K ./Docs
2.0G ./tmp
1.0K ./Movies
19M ./Music
11M ./Pictures
64K ./etc
2.0G . 


The first line tells you that I am at the /media/x.
The final line says "2.0G .", this means that this folder all files in it and subfolders are with total size of 2.0G.
This was the bug I am talking about.
Because the files and folders are 2.0G but "df -h" says that they are totally "2.7G".

If you want I can put a screenshot from my GNOME too, but I thought that it is clear what is the problem.

---

### Post by meng on 2006-10-14
I apologize for misunderstanding how "du --max-depth" works - my inexperience I'm afraid - on reading yet again, I guess that your post is fairly clear on this. Discrepancies between df and du are well recognized, and depend somewhat on what filesystem is used. I haven't seen a uniform solution posted about this. It is a problem beyond my comprehension, and I'm sorry to have wasted your time.

---

### Post by dinamic on 2006-10-14
Don't worry man.. I am just searching for a suggestion/solution.
I am using EXT3 by the way. I thought this is the perfect filesystem for Linux, but it seems that it is not.
Thank you for your efforts.

---

### Post by dinamic on 2006-10-16
I have made some tests, to locate the issue.
And it seems that it is somethink related to "rTorrent", this is console torrent client.
I have almost removed everything from the drive, and it stills shows me 100% usage, then I have stopped the torrent client - and *bang* it was on 50% usage.
Damn torrent client ](*,) ](*,) :evil: :-#

---

