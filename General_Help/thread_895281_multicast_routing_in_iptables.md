---
title: "multicast routing in iptables?"
date: 2008-08-20
forum: General Help
---

### Post by bemular on 2008-08-20
I have this routing setup involving Apache, Tomcat and mod_jk which seem to be working just fine. I followed the steps on this site:

[http://www.kandysoftwareinc.com/tech-articles/apache-tomcat-cluster-load-balancing-using-mod_jk]("http://www.kandysoftwareinc.com/tech-articles/apache-tomcat-cluster-load-balancing-using-mod_jk")

My problem is that whenever the machine restarts, the iptables (aka default firewall) goes on, thus making my webapp inaccessible, until I manually turn the iptables off again. I've read some and thought about actually having iptables to be not included at startup but I was hoping for an alternative so I would not entirely turn off the firewall.

---

