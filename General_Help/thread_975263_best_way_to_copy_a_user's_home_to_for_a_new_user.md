---
title: "best way to copy a user's home to for a new user?"
date: 2008-11-08
forum: General Help
---

### Post by graysky on 2008-11-08
I have my user account setup the way I like it (gnome widgets, compiz-fusion settings, shortcuts, etc.) and I'd like to make a 2nd user and then totally copy my settings as the default for the 2nd user.  I made the new user, but is what I want to acomplish as easy as copying my user's home dir on top of the new user's home dir and changing owners like this:

```
# cp -r /home/user1 /home/user2
# chown -R user2:user2 /home/user2/*
```

Am I missing something or will that work?

---

### Post by pastalavista on 2008-11-08
I think it would work (I'm no expert) if you are root. Use sudo...

---

### Post by cubeist on 2008-11-08
I have always used:
```
sudo cp -ax /user1 /user2
```

Found this in a tutorial somewhere on these forums...

---

