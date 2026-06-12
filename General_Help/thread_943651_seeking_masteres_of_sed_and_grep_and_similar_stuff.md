---
title: "seeking masteres of sed and grep and similar stuffs"
date: 2008-10-10
forum: General Help
---

### Post by pyrokenx on 2008-10-10
I have some really big documents containing over 800+ emails.  I need to get just the e-mails out of them and into a separate file.

Any ideas how I´d accomplish this?

---

### Post by iponeverything on 2008-10-10
> **pyrokenx said:**
> I have some really big documents containing over 800+ emails.  I need to get just the e-mails out of them and into a separate file.

Any ideas how I´d accomplish this?

What is the format of the files. What created them?

---

### Post by pyrokenx on 2008-10-10
> **iponeverything said:**
> What is the format of the files. What created them?

The files are a huge list of business data each line has a time and date, a method of payment status of order a username, an order number, and the email of the customer.

The file is in excel but I intend to put it in plain text if thats easier.

everything is in one column unfortunately.

I need a way to get all parts that conform to ¨*@*.*¨  and nothing else in the line.

---

### Post by iponeverything on 2008-10-10
> **pyrokenx said:**
> The files are a huge list of business data each line has a time and date, a method of payment status of order a username, an order number, and the email of the customer.

The file is in excel but I intend to put it in plain text if thats easier.

everything is in one column unfortunately.

I need a way to get all parts that conform to ¨*@*.*¨  and nothing else in the line.

just pulling email addresses out is easily done with a short perl script.. something like this.. though you will need to fix the regex up a bit.

```
#!/usr/bin/perl
while(<>){
     chomp;
     /.*(\w+\@\w+\.\w+)\s.*/;
     print "$1\n";
}
```

---

### Post by taladan on 2008-10-10
I would probably do something a little more round about, but I'm used to using vim for weird tasks like this, if you can get it all into a text file, and if there's a space (' ') character seperating each field, I would run a command in vim:

```
:%s/ /^M/g
```

^M is actually hitting CTRL+V and then hitting Enter/Return

This should put all single entries seperated by a space on its own line.  Then :wq the file and do something like this:

grep @ file.txt >emails.txt

That'll pull any line with an @ symbol in it out and put it in a file named emails.txt.  Not a perfect solution if @ exists anywhere in that file besides an email address.  

Just a different solution,

Tal

---

