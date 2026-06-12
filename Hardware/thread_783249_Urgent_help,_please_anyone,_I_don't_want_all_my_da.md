---
title: "Urgent help, please anyone, I don't want all my data lost!"
date: 2008-05-05
forum: Hardware
---

### Post by go7Ul1ai on 2008-05-05
Hello,
I have been messing around with my system and forgot to do a back up, I managed to copy some files that will help me set up the customising for next time I install Ubuntu (I format and reinstall a lot, an obsession of mine) but I don't have the permissions to copy over the Pictures folder, I don't have these pictures any where else and all I want to do is copy the pictures to another drive (im using my iPod for this) but it just wont let me. I have hundreds of photos and they have great sentimental value to me,
can anybody help me out? I'm desperate.

Thanks for any help in advance,
Lee

---

### Post by pytheas22 on 2008-05-05
What are the permissions on the directory where the folder is stored?  If you don't know, run the command

```
ls -l NAME-OF-DIRECTORY
```

---

### Post by starcannon on 2008-05-05
This should do it,

```

sudo cp -R /your/picture/folder /some/place/safe

```

You may want to set permissions for easier use later as well.

```

man chmod

```

---

