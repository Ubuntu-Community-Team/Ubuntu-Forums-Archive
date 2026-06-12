---
title: "No-IP Port 80 Redirect Question"
date: 2008-07-11
forum: General Help
---

### Post by rendo on 2008-07-11
Alright.

I've set ports.conf in the apache2 folder to listen to port 81.  I've port forwarded port 81 to my IP through the router and I've setup a no-ip account to redirect traffic through DNS.

I have 2 redirects setup.  One just as a hostname, the other for my website since my new ISP has blocked port 80.  

Now, here lies my problem.  Traffic can get to the website and my forums just fine.  However, when attempting to LOGIN, LOGOUT, or anything similar in nature to that, it goes to the hostname, which of course uses port 80 by default and therefore the site cannot connect.  I'm not exactly sure why this is as everything else seems to work.

The redirect is dbiforums.bounceme.net so if anyone can help me figure this out, much props.  I've gone over all the configuration files and still can't seem to figure it out. 

Much thanks.

---

### Post by rendo on 2008-07-11
N/M Folks.  I found there was a configuration for the forum for the port, so it kept trying to use port 80.  <3  Thanks for making me think harder with my silly post! :D

---

