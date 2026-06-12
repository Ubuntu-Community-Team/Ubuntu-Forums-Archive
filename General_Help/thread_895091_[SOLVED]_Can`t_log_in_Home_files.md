---
title: "[SOLVED] Can`t log in Home files"
date: 2008-08-19
forum: General Help
---

### Post by madeinbrazil on 2008-08-19
I tried to move /home to a different partition and for some reason it didn`t work. I followed this tutorial - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

So, when I tried to recover I did the steps recommended but when I`m trying to log in, right after I type my password there is an ACCESS DENIED error saying files couldn`t be loaded because I`m not the owner.

How can I place the files back with the right permission settings so that I can everything again? I`m now running on Live CD :(

Help?

---

### Post by meanburrito920 on 2008-08-19
sudo chown -R NEW_OWNER /home/USER

Try that.

---

### Post by madeinbrazil on 2008-08-19
Thanks for the tip! But, I'm being really cautious now. So, just to make sure I don't make things even worse:

- Shall I write this command while running the LiveCD?
- Do I just place this command (copy & paste) or is there any previous command such as mounting the drive where the /home is stored?
- Should I replace any of the words in this command, like "New Owner" and "User"?

Sorry if these are lame questions, I just want to be sure I don't do anything wrong again :)

---

### Post by meanburrito920 on 2008-08-19
It doesnt matter where you run it from unless the liveCD doesnt let you sudo. then try it on the console in recovery mode on your installed distro. if the command fails, try mounting the drive where /home is stored and doing it again. and yes, replace NEW_OWNER with your user name and USER with your user name. Your questions aren't lame, its always good to be cautious.

---

### Post by madeinbrazil on 2008-08-20
My username is `danilo`, so when I run

```

ubuntu@ubuntu:~$ sudo chown -R danilo recovery/home/danilo

```

I get
```

chown: invalid user: `danilo'

```

I`m going to try now the recovery console you mentioned.

Thanks a bunch for all the help!! I`ll post here soon to see what came up.

---

### Post by madeinbrazil on 2008-08-20
In the recovery console, IT WORKED!!! :)

You're awesome!!! Thank you, thank you, thank you!!

---

