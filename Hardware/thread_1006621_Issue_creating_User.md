---
title: "Issue creating User"
date: 2008-12-09
forum: Hardware
---

### Post by anantgowerdhan on 2008-12-09
Hi,

I just installed Ubuntu on my office laptop and I was trying to create a username like this <first name>.<last name> but Ubuntu doesn't allow me to do that. I was able to create such user in OpenSuse. 

Please let me know the solution if anyone has done it before

Regards,
Anant

---

### Post by taurus on 2008-12-09
You can create a new user from System -> Administration -> Users and Groups unless you are running a server, then you would use the useradd command.

```
man useradd
```

---

### Post by anantgowerdhan on 2008-12-09
Hi Taurus,

I think you did not read my question properly. I know how to create user but the Ubuntu system is not allowing me to create a user with the following naming convention.

<firstname>.<lastname> i.e. john.paul

I can creat a user johnpaul but not like john.paul

---

### Post by capn_hector on 2008-12-09
when you try to add the user first.last you get ```
adduser: Please enter a username matching the regular expression configured
via ...
```

you can change the regex in the /etc/adduser.conf to included what you want or use the --force-badname operand to force the user name

---

### Post by anantgowerdhan on 2008-12-11
hi capn_hector,

I did not understand what you asked me to do. I opened the adduser.conf and there is a regular expression line as well but I dont know what to do with that. I added "." in that expression and saved the file and tried to create user with the name **john.paul** but it is behaving the same. It is not letting me use "." in between the username.

I would greatly appreciate if could explain me the process..

regards,
Anant

---

### Post by capn_hector on 2008-12-11
you need to uncomment the line and add the . so it looks like this
```
# check user and group names also against this regular expression.
NAME_REGEX="^[a-z][-a-z0-9]*\.$"

```

---

### Post by anantgowerdhan on 2008-12-12
I did it but still it is not able to create a user with the "."

---

### Post by capn_hector on 2008-12-12
if you use the --force-badname it will create the user and you dont need to mess with the name_regex however the name_regex would be more elegent ```
sudo adduser --force-badname <user>.<name>
```

---

