---
title: "How to install Java SE 6 on ubuntu?!?!"
date: 2008-08-01
forum: General Help
---

### Post by xspikeyhairx on 2008-08-01
Ok so I have just installed Ubuntu on my computer and I am trying to play RuneScape. I need Java SE 6 and I am trying to find a way to install it. I have downloaded both the versions from the Java Sun website and I have absolutely no idea how to install it. Could someone please help me with this.

---

### Post by ibutho on 2008-08-01
Hi.

Follow the instructions as [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java). Post back if you need more help.

---

### Post by Sef on 2008-08-01
Easy way to install Java:

Applications > Add/Remove > Show: Change to 'All Available Applications' > Search: Sun Java 6 > Click on top box > apply changes > apply > close

---

### Post by tinny on 2008-08-01
> **Sef said:**
> Easy way to install Java:

Applications > Add/Remove > Show: Change to 'All Available Applications' > Search: Sun Java 6 > Click on top box > apply changes > apply > close

Does this enable the "multiverse" repository automatically if you havent already? @OP you need the "multiverse" repository for Sun Java 6.

Another way to install Sun Java 6 if you are happy with the command line...

To install the Sun Java environment...

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin

```

Then to check your install

```

java -version

```

If it all worked you should see something like this

```

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```

---

