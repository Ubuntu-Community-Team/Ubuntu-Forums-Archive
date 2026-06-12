---
title: "[SOLVED] Samba + NIS + Home Folders"
date: 2008-07-14
forum: General Help
---

### Post by chrislynch8 on 2008-07-14
Ok,

So I create all users on server01 and using NIS I send them to all other servers. On server02 I create their samba user accounts if required. Even though their Samba account is created on server02 their home folders are on server01.

I have a folder called centusrs on server01 that hold all home folders and using autoFS this is linked to server02 - on server02 the path to john home folder would be /home/centusrs/centusrs/john. On server01 this is /home/centusrs/john.

Because I create the user on server01 and give him the home location of /home/centusrs/centsrs/john I was hoping to use the "usermod" on server02 to tell samba that johns home folder is /home/centusrs/centusrs/john, but because I use NIS usermod cannot find john in passwd!!!!

Is their any way to tell usermod that the user accounts are in the NIS maps???

Rgds
Chris

---

### Post by justleen on 2008-07-14
yea, with the yp (yellow pages) tools AFAIK.

---

### Post by chrislynch8 on 2008-07-14
> **justleen said:**
> yea, with the yp (yellow pages) tools AFAIK.


just before I start looking through more manauls and documentation - I assume (like a complete ****) that AFAIK is not the tool name but as far as you know!!!! Don't laugh at me I'm new to NIS so it might be for all I know....:lolflag:

Rgds
Chris

---

### Post by justleen on 2008-07-14
yp is the tool :)
yp-tools... 

but im working in an enviroment where NIS is already setup, so im not sure how the to link...

---

### Post by chrislynch8 on 2008-07-14
Sadly I've done a bit more reading and it appears that usermod recognises NIS maps but it will only work will local users....

I little bit of rethinking is required,

Thanks
Chris

---

### Post by chrislynch8 on 2008-07-14
Hi,

Just for any one how has this issue - I solved it. I just changed the link from /home/centusrs to /home. This way the users home directory sent out with NIS will be correct.

Rgds
Chris

---

### Post by cszikszoy on 2008-07-14
It's a good idea to mark the thread as solved under thread tools.  This helps other people searching with a similar problem.

---

### Post by chrislynch8 on 2008-07-14
Thanks,

I was wondering how to do that

Rgds
Chris

---

