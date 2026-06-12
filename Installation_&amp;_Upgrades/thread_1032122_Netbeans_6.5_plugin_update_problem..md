---
title: "Netbeans 6.5 plugin update problem."
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by harsha.angadi on 2009-01-06
I have installed netbeans 6.5 on Ubuntu 8.04 LTS.Everything is working fine, but for plugin updates i am getting the below error.

Unable to connect to the NetBeans because of java.net.UnknownHostException: updates.netbeans.org

And

Check your proxy settings or try again later. The server may be unavailable at the moment. 
You may also want to make sure that your firewall is not blocking network traffic.

I am not using any firewall and my internet is working fine for other things.
On opening of netbeans it should show the updates and recent news related to netbeans there i am getting "cannot connect to internet."I have set "no proxy" in my netbeans configuration as i do not use any of proxy settings.Please help me in this regard.
Thanking You,

---

### Post by paris_alex on 2009-01-06
that's a very strange problem... can you access updates.netbeans.org from browser? i get a html page with a dot (.) which means i can access it.

give it another try?

---

### Post by harsha.angadi on 2009-01-06
No,through browser every thing is working fine but only through netbeans i am not able to connect internet.I dont know what is the problem.
Thanking you,

---

### Post by paris_alex on 2009-01-07
Assuming Netbeans' proxy settings is 'use system settings'... check Gnome's "System > Preferences > Network Proxy" and make sure it is also not using any proxy.

If this does not help... i'm running out of idea.. hehe.. good luck!

---

### Post by harsha.angadi on 2009-01-07
It is set to Direct internet Connection.Do you think is there any problem with netbeans version or any compatiblity problem. please read the problem statement one more time and help me out.
Thank you,

---

### Post by paris_alex on 2009-01-07
try accessing the Internet with other java based programs... like.. er.. let's see... Juice (podcast), RSSOwl, Vuze (Azureus)?

guessing somehow java is not allowed to access the Internet...but you got to make sure your netbeans installation is using the same JVM.

long shot... but well, at least this is how i would diagnose. Good Luck!

---

### Post by Vladi2009 on 2009-07-30
> **harsha.angadi said:**
> I have installed netbeans 6.5 on Ubuntu 8.04 LTS.Everything is working fine, but for plugin updates i am getting the below error.

Unable to connect to the NetBeans because of java.net.UnknownHostException: updates.netbeans.org

And

Check your proxy settings or try again later. The server may be unavailable at the moment. 
You may also want to make sure that your firewall is not blocking network traffic.

I am not using any firewall and my internet is working fine for other things.
On opening of netbeans it should show the updates and recent news related to netbeans there i am getting "cannot connect to internet."I have set "no proxy" in my netbeans configuration as i do not use any of proxy settings.Please help me in this regard.
Thanking You,

Seems to be somehow a DNS issue inside NetBeans/Java system.. It happened to me as well when I changed to Ubuntu 9.04 .. A compromised solution is to insert in /etc/hosts:
72.5.124.114    updates.netbeans.org
66.199.229.210  plugins.netbeans.org
This worked for me .. as last resort..

---

### Post by harsha.angadi on 2009-07-31
Thanks for the solution.

---

