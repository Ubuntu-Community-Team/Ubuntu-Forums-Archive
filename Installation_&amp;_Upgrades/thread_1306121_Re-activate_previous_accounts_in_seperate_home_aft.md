---
title: "Re-activate previous accounts in seperate /home after 9.10 fresh install"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by wiebeest on 2009-10-30
Hello folks,

Freshly installed Karmic Koala yesterday. I'm very satisfied with it so far, but...

As the title suggests I run into a particular problem. 

My **/home **folder is on a different partition.
As I had done with the install of Jaunty before, I selected to format **/** and **swap**, 
but keep away of **/home**, only selecting to mount that as **/home**, but not reformat.
I then created a new account under a different name and installed Karmic.

After install my former **/home** is indeed there, the previous 2 accounts being visible and accessible, 
but I can't seem to re-activate those accounts on there. 

At the logon it only shows my new account not the other two.

How do I fix this?

Help very much appreciated. Thanks beforehand.

Sincere greetings,

Wiebeest

---

### Post by fancypiper on 2009-10-30
You will need to create the user accounts again with "User and Groups" utility.

Then, you will need to change ownership of the old folder as it will have the old ownership

sudo chown -R <username>.<username> /home/username.

Then, they should show up in the login screen.

---

### Post by wiebeest on 2009-10-30
> **fancypiper said:**
> You will need to create the user accounts again with "User and Groups" utility.

Then, you will need to change ownership of the old folder as it will have the old ownership

sudo chown -R <username>.<username> /home/username.

Then, they should show up in the login screen.

Hey, thanks for the quick reply. 

But the problem persists, for if I try to re-create an account for one of the previous users under **User and groups** in the advanced tab it nags about that the personal directory already exists and I have to choose another. 

Must I perhaps do that *chown command* you suggested beforehand, or something?

---

### Post by fancypiper on 2009-10-30
I stated it backwards, change ownership, then create user.

Yep, that's what it's griping about.

sudo chown -R <username>.<username> /home/username

should fix it.

---

### Post by wiebeest on 2009-10-30
> **fancypiper said:**
> I stated it backwards, change ownership, then create user.

Yep, that's what it's griping about.

sudo chown -R <username>.<username> /home/username

should fix it.

So, let me get this right. Is that correct, with <username>.<username>?

If the user is Betsy. And her directory is /home/betsy.
Then I should type:
```
sudo chown -R betsy.betsy /home/betsy 
```

Are you sure that should be it? 

Because I know the folder /home/betsy is there.
But if I type ```
sudo chown -R betsy.betsy /home/betsy 
``` as a command it states: 
```
chown: invalid user: 'betsy.betsy'
```

---

### Post by DenysT on 2009-10-30
Try using <username>:<username>. That is the info I found in pyschocats tutorial.

---

### Post by fancypiper on 2009-10-30
What I actually did was to chown to my current user, then change the name of the folder, then create the new user, chown of the old name to the newly created user and then copied folders and files over as I needed them.

Awkward, but it got the job done.

---

### Post by wiebeest on 2009-10-30
> **DenysT said:**
> Try using <username>:<username>. That is the info I found in pyschocats tutorial.

**I solved it!! **:D

But... in a different way:

As *ROOT* I checked: **etc/passwd**
The new user was not there (obviously).

Then with:
```
sudo adduser <username>
```
I did manage to create the account. Then afterwards I checked **etc/passwd** and this time the user was there. 
Logged in as that user, which now worked, so the problem was solved through these steps.

So my guess is that the graphical *"User and Groups"* utility contains a bug, so that it can't create a new user account if the user already exists in /home/<username>

Because doing exactly the same thing through the good old terminal succeeded whilst the graphical shell refused to do so.

Solved!

---

### Post by fancypiper on 2009-10-30
Don't fear the terminal, that's where the power is!

---

### Post by wiebeest on 2009-10-30
> **fancypiper said:**
> Don't fear the terminal, that's where the power is!

Indeed. Thanks for the help.

---

### Post by fancypiper on 2009-10-30
Don't forget to [Mark Your Thread as [SOLVED] After Getting Your Answer](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

### Post by n411303 on 2009-11-02
> **wiebeest said:**
> **I solved it!! **:D

But... in a different way:

As *ROOT* I checked: **etc/passwd**
The new user was not there (obviously).

Then with:
```
sudo adduser <username>
```
I did manage to create the account. Then afterwards I checked **etc/passwd** and this time the user was there. 
Logged in as that user, which now worked, so the problem was solved through these steps.

So my guess is that the graphical *"User and Groups"* utility contains a bug, so that it can't create a new user account if the user already exists in /home/<username>

Because doing exactly the same thing through the good old terminal succeeded whilst the graphical shell refused to do so.

Solved!

THIS IS FANTASTIC!!!
WORKS LIKE A DREAM!!

Tell EVERYONE this is the way to clean install Ubuntu every six months without user profile/account problems.  

Thank you very much.

---

### Post by donato roque on 2009-11-02
Thank you very much for this thread.  I've been looking for the solution too.  Terminal rules!

---

### Post by fancypiper on 2009-11-02
I think you mean "bash rules!"

---

