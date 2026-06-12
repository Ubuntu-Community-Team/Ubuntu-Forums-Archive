---
title: "bizar root problem"
date: 2008-07-14
forum: General Help
---

### Post by gregasus on 2008-07-14
I have a rather bizar problem, my root password sometimes doesn't work.
And I do mean sometimes.
When I'm promted for it like when using synaptic it works.
But when I tried to log in as root it didn't, I'm sure I typed it correct I tried like 20 times or so (while typing this I tried an additional 2 times)
Having installed Linux just recently I'm not sure what to do, any help is welcome.

Thanks in advace

---

### Post by tszanon on 2008-07-14
You can't login as root in a default Ubuntu installation. The root user login is disabled. It's for security purposes.

If you need to do anything as root, use **sudo** or **gksu**.
< rest of message removed>

---

### Post by snowpine on 2008-07-14
> **gregasus said:**
> I have a rather bizar problem, my root password sometimes doesn't work.
And I do mean sometimes.
When I'm promted for it like when using synaptic it works.
But when I tried to log in as root it didn't, I'm sure I typed it correct I tried like 20 times or so (while typing this I tried an additional 2 times)
Having installed Linux just recently I'm not sure what to do, any help is welcome.

Thanks in advace

Hi Gregasus, you did not mention which flavor of Linux you are using, so I will assume Ubuntu (since this is the Ubuntu forum). You should not log in as root in Ubuntu (for security reasons); instead, you should use the 'sudo' command in front of anything that requires root access. For example 'sudo apt-get update'.

It's against forum rules for anyone to give you advice on how to get around this important security feature. :)

---

### Post by kk0sse54 on 2008-07-14
You are not supposed to be able to log in as root which is why you use sudo in the terminal in order to gain temporary root access. What exactly were you trying to do by logging in as root?

---

### Post by Vivaldi Gloria on 2008-07-14
> **gregasus said:**
> I have a rather bizar problem, my root password sometimes doesn't work.
And I do mean sometimes.
When I'm promted for it like when using synaptic it works.
But when I tried to log in as root it didn't, I'm sure I typed it correct I tried like 20 times or so (while typing this I tried an additional 2 times)


In a default ubuntu install the root password is a random hidden password. You can use your own password to use sudo & gksudo because the first user created has admin rights. But that pswd it your pswd, not root's.

---

### Post by coffeecat on 2008-07-14
> **gregasus said:**
> I have a rather bizar problem

You don't have a problem at all. Everyone's already explained, but you might like to read the official Ubuntu explanation [here]("https://help.ubuntu.com/community/RootSudo").

---

### Post by tszanon on 2008-07-14
> **snowpine said:**
> It's against forum rules for anyone to give you advice on how to get around this important security feature. :)

Sorry, I wasn't aware of that. Code removed.
Thanks for the tip.

---

### Post by gregasus on 2008-07-16
Thanks for the help I didn't know that.
I was trying to move a file, can't be so to do in the commandline.

Thanks for the explanation everyone.

---

