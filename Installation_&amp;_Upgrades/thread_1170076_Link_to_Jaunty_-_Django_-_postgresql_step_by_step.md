---
title: "Link to Jaunty - Django - postgresql step by step?"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by erik.reppen on 2009-05-25
Background: I'm pretty new to Linux/Unix, but grew up on DOS so command lines aren't scary, but bad directions with no version numbers or even dates attached to them are. I've got pretty far in Django but I can't seem to get a DB working with Django to save my life. I'm also more of a front end than back end developer but I built DBs with mysql in school a couple years ago and I get the modelling aspect of DBs jut fine.

I'm mostly confused on creating a DB and establishing proper user authentication. People just throw a whirlwind of Linux commands for user stuff without really explaining what it is you're doing and I'm pretty sure some stuff out there is just plain wrong because of the results you get (like getting a psql interactive prompt with a name that's supposed to be the user when their examples show it being template1).

My assumption upon installing postgres was that the user "postgres" is the default super user but that you're supposed to avoid using that to avoid breaking stuff. Now I've actually changed the pword of that a few times and I've tried setting up users in both postgres and the Linux command prompt that have identical passwords and nothing seems to take. I just can't get my DBs to take. It's getting seriously frustrating.

Is anybody aware of a step by step for this process that actually works? I'm mucking about with views and url configs in Django just fine. It's building tables off the models that's hosed. I'll go through these steps for creating users and keep getting the same messages over and over again that user authentication has failed.

---

### Post by ssavelan on 2009-06-04
I like these directions and I am about to adapt them to postgis/jaunty.  The principles are the same.  I think the section on postgres is particularly good and still applicable in jaunty.

[http://www.punteney.com/writes/setting-django-slicehost-ubuntu-hardy-postgres-apa/](http://www.punteney.com/writes/setting-django-slicehost-ubuntu-hardy-postgres-apa/)

---

