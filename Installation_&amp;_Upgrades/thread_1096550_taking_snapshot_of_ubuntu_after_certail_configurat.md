---
title: "taking snapshot of ubuntu after certail configuration"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by Shuaib Zahda on 2009-03-15
Dear all

I have a cyber cafe where I install ubuntu on all of the machines. Some clients tend to make changes to the system or install some games and software, etc etc. 

I am looking for a way to install ubuntu and install the applications I want and then take a snapshot of the system.

Later when I restore to this snapshot, I want the changes that were made by the users to be deleted.

Is there a solution or software to do that

Thanks

---

### Post by cariboo on 2009-03-15
I would suggest you not allow your users to install anything. Setup a limited user, then if you  need to allow the limited user to autologin.

Even better is to setup kde kiosk, give your users some eye candy, and lock things down, so they can't change things.

Jim

---

### Post by Shuaib Zahda on 2009-03-15
Hi

Thanks for the reply. I agree with you. However, I do conduct Ubuntu training in the same lab, so the students need to practice the installation and some of them tries to install themes and new stuff. So, I need to restore back to the setup I want which is the default without new installation each time I conduct the training

Thanks

---

### Post by robert shearer on 2009-03-15
would this be of use?

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

it will remaster your install to a iso file or live cd and that is the snapshot you need 
The drawback being that you would need to reinstall from these each time. (though from experience it is a lot faster than a standard Ubuntu install.

---

### Post by Shuaib Zahda on 2009-03-15
Thanks for the tool. This would help me somewhat. It will be great if ubuntu itself has this backup/restore feature.

---

