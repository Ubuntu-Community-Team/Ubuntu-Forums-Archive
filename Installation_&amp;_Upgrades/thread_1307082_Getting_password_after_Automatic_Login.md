---
title: "Getting password after Automatic Login"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Skane2600 on 2009-10-30
When installing Ubuntu you have the option of choosing automatic login instead of creating a password. Later you may need to use your password. Is it possible to find/create a password in this scenario?

Thanks

---

### Post by celtic426 on 2009-10-30
You can set up your password by going to System-Administration-Users and Groups.  Click properties on your name and you will see the password there.

Also for setting up the login screen, go to System-Administration-Login Screen

---

### Post by Skane2600 on 2009-10-30
I don't see my password in the properties and a password is required to access the login screen.

---

### Post by celtic426 on 2009-10-31
> **Skane2600 said:**
> I don't see my password in the properties and a password is required to access the login screen.

Alright, open Users and Groups up and then click the key symbol to make changes and type your password.  Then click on your name in the usernames list.  Then click Properties which is to the right.  In there you should find what you need.

---

### Post by coffeecat on 2009-10-31
@Skane2600, is it that you've forgotten your password and so you can't do any administrative tasks, including resetting your password? It's not quite clear.

If that's the case, you need to boot up into recovery mode and reset it from the command line. Here's how:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Skane2600 on 2009-10-31
> **coffeecat said:**
> @Skane2600, is it that you've forgotten your password and so you can't do any administrative tasks, including resetting your password? It's not quite clear.

If that's the case, you need to boot up into recovery mode and reset it from the command line. Here's how:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I think people are missing the point. If when you install Ubuntu you choose the automatic login option, you *don't* create a password. So I didn't forget my password, I never had one (yes, there might be an internal one, but it isn't displayed). Any solution that requires entering my password is obviously not going to be possible.

It seems to me that this install option should be removed if it requires using the recovery mode to find out what your password is (assuming there's no solution that hasn't been suggested yet).

Obviously I'd advise anyone trying Ubuntu to ignore that option and make sure they create a password so they know what it is when they need it.

Thanks to all who have attempted to answer my question.

---

### Post by coffeecat on 2009-10-31
> **Skane2600 said:**
> I think people are missing the point. If when you install Ubuntu you choose the automatic login option, you *don't* create a password.

No - it is impossible to install Ubuntu without setting a password **unless** you do an OEM install from the alternate CD.

---

### Post by coffeecat on 2009-10-31
OK - I thought I would make this clearer with a screenshot. You have to choose a password (which is also your administrative password) to install Ubuntu. (Except in the case of an OEM install which is an entirely different matter.) This is is the screen where you have to both give the password (twice), **and** choose whether or not to login automatically. Just because you have an automatic login without entering a password does not mean you do not have a password. You cannot get past this screen without setting a password.

---

### Post by Skane2600 on 2009-10-31
I tried to do another install to test your claim and you were correct - I couldn't go beyond that screen without choosing a password. Remembering things that didn't happen - not a good sign :)

Sorry for wasting everyones time. At least if someone is suffering from the same delusion someday they'll be able to search for the answer without embarrassment.

---

### Post by coffeecat on 2009-11-01
> **Skane2600 said:**
>  Sorry for wasting everyones time. At least if someone is suffering from the same delusion someday they'll be able to search for the answer without embarrassment.

No problem. You haven't wasted anyone's time; don't be embarrassed. You're not the first to not remember that they had to assign a password. I can assure you that you won't be the last. :) Put it down to unfamiliarity with a new environment.

By the way I've edited my last post and changed the image to an uploaded one. The linked image was from a Jaunty install. I just happened to be doing a new Karmic install and I thought it would be better to show a Karmic one.

All this editing and posting was done from the Karmic live CD. Ain't Ubuntu marvellous? :p

---

