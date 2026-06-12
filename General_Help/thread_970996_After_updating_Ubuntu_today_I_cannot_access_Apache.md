---
title: "After updating Ubuntu today I cannot access Apache via IP any more only local access?"
date: 2008-11-04
forum: General Help
---

### Post by Presto-X on 2008-11-04
Hello everyone, I'm new to Ubuntu, so far it has been very stable and very reliable... I have been using this system for about two months now with out any problems it's been great!

Ok today I logged in and I noticed Ubuntu had 12 updates today I updated and restarted, once I logged back in I can access apache locally but if I type in the servers IP address I get a 404...

I'm wondering if one of the new updates closed port 80? I'm not sure how to even check this... Where do I need to start testing at???

Thanks for any help you guys can provide.

---

### Post by cmnorton on 2008-11-05
Start by looking in /etc and seeing if files like /etc/hosts were renamed. You're looking to see if your hosts file changed. Also, check to see that apache is running, ps -ef | grep apache.

Also, check if apache's conf file was also were renamed (/etc/apache2/apache2.conf)?

---

### Post by KeyserSoze93 on 2008-11-05
And make sure you have the same IP ```
ip addr
``` as you had before.

---

