---
title: "firefox ports"
date: 2008-07-28
forum: General Help
---

### Post by timboellis on 2008-07-28
I am using the latest version of firefox and need to access port 6000 so how do I unblock this on firefox

---

### Post by dexter.deepak on 2008-07-28
cant understand you perfectly.
firefox is a client,and not a server..so you can access any server's port 6000 by just appending :6000 to the url
like for your own computer (localhost),type the following in address bar
```
localhost:6000
```
but this would work only if some service is listening to port 6000.

---

### Post by tamoneya on 2008-07-28
the port blocking is most likely coming from the server side.  Can you confirm that the port is correctly opened and forwarded with an nmap scan first.

---

### Post by timboellis on 2008-07-28
When I used firefox on a windows machine I was able to unblock this port.

If i go to localhost:6000 in Internet explorer all okay but firefox blocks this port a a known security issue.

I just need to unblock it from firefox but unsure how to in the new version 3

---

### Post by timboellis on 2008-07-28
I just now found the command to do this

Enter about:config in the browser.

2. A list of settings will be shown.  Right click the web page, select New and click String.

3. Enter network.security.ports.banned.override in the dialog and click OK.

4. Then enter 6000 and click OK.

5. The setting will be added to the list. You can now use Firefox to access port 6000.

---

