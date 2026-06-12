---
title: "[SOLVED] Apache .htpassword file"
date: 2008-10-09
forum: General Help
---

### Post by timboellis on 2008-10-09
A while ago a greated a .htaccess and a .htpassword file in order for me to password protect my main directory, however need to change the password but as it is encrypted in the file not sure how to change it

how do i change the file in order to specify a new username and password?

---

### Post by bodhi.zazen on 2008-10-09
[http://httpd.apache.org/docs/1.3/programs/htpasswd.html](http://httpd.apache.org/docs/1.3/programs/htpasswd.html)

use the -c flag to make a new file.

htpasswd user , without the -c , to add a user

---

### Post by timboellis on 2008-10-09
Thanks spot on

---

