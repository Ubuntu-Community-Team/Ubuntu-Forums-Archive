---
title: "Auto Logon in SSH ??"
date: 2008-07-31
forum: General Help
---

### Post by matey3 on 2008-07-31
Hi;
Does anyone know how I could insert a line in my backup script for the backup files to store on a remote server via ssh?
You know when you ssh to another server it will ask you to login first.(May be even use scp??).

 I know how to do ssh -l to input the username (ie. root) but I do not know how to also put the password in my script!?
I'd like to back up my servers at night when no one is on.

Thanks in advance for any info/links.

---

### Post by treymul on 2008-07-31
set up public key authentication, that way there won't be any need for passwords(its also supposed to be much more secure).

[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

---

### Post by bodhi.zazen on 2008-07-31
> **matey3 said:**
> Hi;
Does anyone know how I could insert a line in my backup script for the backup files to store on a remote server via ssh?
You know when you ssh to another server it will ask you to login first.(May be even use scp??).

 I know how to do ssh -l to input the username (ie. root) but I do not know how to also put the password in my script!?
I'd like to back up my servers at night when no one is on.

Thanks in advance for any info/links.

Rather the doing that you might want to look at expect :

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

    [http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

Sample script for ssh:

>         #!/usr/bin/expect
        #Set the timeout time
        set timeout 60
        #Starts the SSH session. Change "username", "host" and "command"
        spawn ssh -XfC -c blowfish -l username host command
        #Begins the password prompt
        expect "password: $"
        #User Password. Replace "username_password" with your password.
        #Leave "\n", as it is a break, or enter, which submits the password.
        send "username_password\n"
        #Sends back to prompt
        expect "%$"

I can not recall, but I think I got that script from DrSmall, you will need to adopt it to your situation.

---

### Post by treymul on 2008-08-06
I am just curious, why would that be better than using public key authentication?

---

### Post by bodhi.zazen on 2008-08-07
> **treymul said:**
> I am just curious, why would that be better than using public key authentication?

Not better , just different. I personally do not like keys with no password, others do ont like placing their password in  a file, but the choice is up to you.

---

### Post by treymul on 2008-08-07
Thanks

---

### Post by matey3 on 2008-08-12
oops i got it..
' sing quote not " double

---

