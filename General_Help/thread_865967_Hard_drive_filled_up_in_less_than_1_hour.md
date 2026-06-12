---
title: "Hard drive filled up in less than 1 hour"
date: 2008-07-21
forum: General Help
---

### Post by mkvnmtr on 2008-07-21
It is time to ask for help. I have Dapper on a 4 year old Ibook with a little more than 15 Gb for Ubuntu .This morning when I booted within an hour my particion was 98% full.Should be less than 3 Gb with home included. I Deleted my stuff in home and gained less than 1 Gb. I am studying the logs but have very little experience. I think I am seeing that a root user did it but I am not sure if it was something the system did or an intrusion from outside. I don't know how to see what is taking up the space so I have no idea how to proceed. Maybe somebody could give me an idea how to see the size of files to find where the problem is. I hope I have explained this so you can understand the problem.

---

### Post by Yannick Le Saint kyncani on 2008-07-21
> **mkvnmtr said:**
> This morning when I booted within an hour my particion was 98% full.

xdiskusage can show you what is eating all this space. It's a graphical app and given that $HOME is not taking all space, you would want to run it as root.

For a console app, you can use "sudo du -ksx /* | sort -n". This will show you which directory is eating all this space. From then on, if for example /var is taking all space, you can "sudo du -ksx /var/* | sort -n" and work your way toward the culprit.

Hope this helps.

---

### Post by mkvnmtr on 2008-07-21
Sounds like that is what I am looking for. Thanks I will start it now.

---

### Post by mkvnmtr on 2008-07-21
Thank you, your command got me the information I needed. Looks like I messed up adding software that didn't go together well. Boy this is fun, now I get to reinstall and start messing up my system again.

---

### Post by Titan8990 on 2008-07-21
There shouldn't be any reason to reinstall. Have you considered removing the files that you don't need?

Time to leave the Windows mindset of "reformat" behind you.

---

### Post by Yannick Le Saint kyncani on 2008-07-21
> **Titan8990 said:**
> There shouldn't be any reason to reinstall. Have you considered removing the files that you don't need?

+1 to that.

Of course, this might serve as a perfect excuse to go the hardy way :)
New and shiny software :popcorn:

---

### Post by damis648 on 2008-07-21
> **Yannick Le Saint kyncani said:**
> +1 to that.

Of course, this might serve as a perfect excuse to go the hardy way :)
New and shiny software :popcorn:

+1 Try out Hardy. Several years newer. :popcorn:

---

