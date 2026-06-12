---
title: "Remove password requirement"
date: 2008-12-01
forum: General Help
---

### Post by lavinog on 2008-12-01
I built a computer for my son, who knows how to use a mouse, but doesn't understand passwords.

For the most part the auto login works for him, but if he logs out, he has to put in a password to log back in.

Is there a way to remove the password requirement, or allow a zero length password.
Security is not a concern for this computer.

---

### Post by cmnorton on 2008-12-01
It is highly unrecommended, frowned up, and not a good thing. You are better off with a small password, like three letters or three numbers.

However, and please proceed at your own risk:

1) As root, make a copy of  /etc/shadow, like cp /etc/shadow /etc/shadow.install
(ls -l /etc/shadow), if there are no write permissions for root, set them (chmod 600 /etc/shadow, and make sure to put the permissions back when you're done.)

I did not have to do this on my Ubuntu system; I did have to do it on a Fedora system.

2) As root, edit /etc/shadow

3) Locate your son's login.

4) Remove all text (the encrypted password) from between the first and second colons (:) starting from the left hand side. Essentially, you are removing the encrypted text from the second field from the left.

5) Save the file.

6) Try logging in as your son; only the username should be accepted. That is, you'll never be prompted for a password.

---

### Post by bodhi.zazen on 2008-12-01
No, you have to put in the hash for an empty password.

I agree, best teach your son how to log in, this is a fairly basic function.

---

### Post by hayden92 on 2008-12-01
What you could do is set the password as his username e.g:

usrname: bob
passwrd: bob

And just tell him that he has to type in his name twice
You did say that he understands usernames so this should go down easily.

Hope that helps,
Hayden

---

### Post by lavinog on 2008-12-01
He is 3 and doesn't know how to use the keyboard yet...only the mouse.

---

### Post by aysiu on 2008-12-01
You can set up in System > Administration > Login Window a timed login (as opposed to an automatic login).

---

### Post by defishguy on 2008-12-01
You could use a small and cheap usb flash drive to authenticate him and not worry about a password that is too simple.


[**_Here_**]("http://pamusb.org/") is the project homepage.  The instructions for getting it working are pretty simple.

Everything you need is in the repos.

> sudo apt-get install pamusb-tools

Good luck!

---

### Post by lavinog on 2008-12-01
> **hayden92 said:**
> What you could do is set the password as his username e.g:
usrname: bob
passwrd: bob

[QUOTE=cmnorton]
It is highly unrecommended, frowned up, and not a good thing. You are better off with a small password, like three letters or three numbers.[/QUOTE]

> Password is too short: User passwords must be longer than 6 characters and preferably formed by numbers, letters and special characters.


I think I found a solution.
/apps/gnome-power-manager/lock/ in gconf-editor has some options to disable the lock when resuming from standby...etc

It might be enough, but I don't understand why there isn't an easy way to create a guest account with basically no permissions

This computer will actually be used by a couple of kids where internet access will be limited to 3 websites.
It is a garbage computer made out of parts people were going to throw away.

---

### Post by lavinog on 2008-12-01
> **defishguy said:**
> You could use a small and cheap usb flash drive to authenticate him and not worry about a password that is too simple.

[**_Here_**]("http://pamusb.org/") is the project homepage.  The instructions for getting it working are pretty simple.

Everything you need is in the repos.

Thank you for the info...I don't think I want to dedicate a flash drive to this computer, but the info will be very helpful for other projects I want to work on.

---

### Post by lavinog on 2008-12-01
> **aysiu said:**
> You can set up in System > Administration > Login Window a timed login (as opposed to an automatic login).

This might work too...I didn't try it because I didn't think I wanted a time delay, but whats another second.

---

### Post by cmnorton on 2008-12-02
> **bodhi.zazen said:**
> No, you have to put in the hash for an empty password.

I agree, best teach your son how to log in, this is a fairly basic function.

Good to know this on Debian systems. On Fedora, it accepted a blanked field.

---

