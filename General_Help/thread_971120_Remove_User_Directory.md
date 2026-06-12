---
title: "Remove User Directory"
date: 2008-11-04
forum: General Help
---

### Post by frank.zappa on 2008-11-04
When I was using Hardy, I created 2 extra users named 'temp' and 'zappa'. I had removed the users using Users and Groups but it did not delete the user's directories. 

I have tried "sudo userdel -r temp" and "sudo userdel -r zappa", yielding "userdel: user temp does not exist" and same for 'zappa'.

How can I get rid of these useless folders?

Edit: nevermind, I just tried "sudo rm -r temp" and it worked. I could have swore that I tried this before and I got an error, I think it was because I didn't add sudo the other time. Sorry for the inconvenience.

---

### Post by bodhi.zazen on 2008-11-04
sudo rm -rf /home/{temp,zappa}

---

### Post by frank.zappa on 2008-11-04
Thanks, I never knew about the '{}' syntax.

---

