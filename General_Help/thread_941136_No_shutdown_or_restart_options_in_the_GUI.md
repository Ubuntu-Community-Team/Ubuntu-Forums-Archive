---
title: "No shutdown or restart options in the GUI"
date: 2008-10-07
forum: General Help
---

### Post by amaruq_atka on 2008-10-07
I really only noticed this after I installed Startup Manager. When I click the little icon on the top panel it shows me, logout, lock, switch, suspend and hibernate, but not shutdown or restart. I went into the authorizations and gave myself the privileges, but they still does not work.

Now, I dont mind using sudo shutdown -h, and sudo restart. But, I really wanted to ween my dad off of windows millennium (he thinks its the greatest thing in the world, dont ask.) and let him have something easy to use and that wont crash, just to check his email, stocks and look up little stuff on the net. (he has zero knowledge of computers.)

---

### Post by Steve1961 on 2008-10-07
> **amaruq_atka said:**
> I really only noticed this after I installed Startup Manager. When I click the little icon on the top panel it shows me, logout, lock, switch, suspend and hibernate, but not shutdown or restart. I went into the authorizations and gave myself the privileges, but they still does not work.

Now, I dont mind using sudo shutdown -h, and sudo restart. But, I really wanted to ween my dad off of windows millennium (he thinks its the greatest thing in the world, dont ask.) and let him have something easy to use and that wont crash, just to check his email, stocks and look up little stuff on the net. (he has zero knowledge of computers.)

Try sudo dpkg-reconfigure gdm

---

### Post by PocketDog on 2008-10-07
[http://justevolvin.wordpress.com/2007/04/28/ubuntu-feisty-fawn-missing-shutdownrestart/](http://justevolvin.wordpress.com/2007/04/28/ubuntu-feisty-fawn-missing-shutdownrestart/)

---

### Post by amaruq_atka on 2008-10-07
> **PocketDog said:**
> [http://justevolvin.wordpress.com/2007/04/28/ubuntu-feisty-fawn-missing-shutdownrestart/](http://justevolvin.wordpress.com/2007/04/28/ubuntu-feisty-fawn-missing-shutdownrestart/)
oh! thanks so much. it wokred!

---

