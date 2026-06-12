---
title: "update users realname"
date: 2008-09-10
forum: General Help
---

### Post by monkeyking on 2008-09-10
Hi I need to update an allready existing users realname to the system.
Not the login name,
just the real name.

btw I should be a commandline tool,
not the graphic users-admin

thanks in advance

---

### Post by Ms_Angel_D on 2008-09-10
Go to system >> Administration >> Users and Groups 

Click unlock and enter your password then select properties for the user you wish to edit. There you can change the Real Name :)

---

### Post by monkeyking on 2008-09-10
:)

As I said, it shouldn't be uses-admin program,
It should be a commandline tool,
but thanks anyway

---

### Post by jerome1232 on 2008-09-10
man useradd, almost the first paragraph
```

 -c, --comment COMMENT
           Any text string. It is generally a short description of the login,
           and is currently used as the field for the user´s full name.
```

So I believe it would if joe bobs login is weeeee
```
sudo useradd weeeee -c "Joe Bob"
```

I believe usermod would do it too although it's -c description doesn't give me the same impression

---

### Post by monkeyking on 2008-09-10
I'm not allowed to change existing users real name using your command,
but thanks.

---

### Post by jerome1232 on 2008-09-10
are you logged in as that user? It won't if you are.

---

### Post by cdenley on 2008-09-10
> **jerome1232 said:**
> man useradd, almost the first paragraph
```

 -c, --comment COMMENT
           Any text string. It is generally a short description of the login,
           and is currently used as the field for the user´s full name.
```

So I believe it would if joe bobs login is weeeee
```
sudo useradd weeeee -c "Joe Bob"
```

I believe usermod would do it too although it's -c description doesn't give me the same impression
You didn't read the manpage close enough.
> 
useradd - create a new user or update default new user information

The command you posted will try to create an account. The poster needs the usermod command.
```

sudo usermod -c "John Doe" jdoe

```

---

