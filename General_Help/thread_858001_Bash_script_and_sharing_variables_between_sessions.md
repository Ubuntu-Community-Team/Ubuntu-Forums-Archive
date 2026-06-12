---
title: "Bash script and sharing variables between sessions"
date: 2008-07-13
forum: General Help
---

### Post by durino13 on 2008-07-13
Hello all,

I want to write a script, which will test, if my key servers are up and running. Script will do a simple ping and if there's no response, mail will be send. 

I am able to do most of it, however I have 1 problem. Once the server is down, I don't want to flood my mailbox with emails. I want send only 1 email and then nothing. 

I was thinking to use environment variables to share parameters between scripts. 

```
if [ "$SENDEMAIL" = "True" ]; then
    #send mail
    export SENDMAIL="False"
else
    #do other stuff
fi
```

My script is driven by CRON running every 5 minutes and it seems to me, that variables will not be preserved between sessions. 

I was also thinking to create some files to share info between sessions, but this doesn't seem to be a nice solution for me.

I am sure, this was solved already before. 

Does anybody has a working example of such script?

Thx for help in advance !!

---

### Post by fahadsadah on 2008-07-13
A file is the simplest way:```

if [ "$SENDEMAIL" = "True" ]; then
    #send mail
    : > ~/.keyservercheckingscript/sendmail.false
else
    #do other stuff
fi
```

Then, if ~/.keyservercheckingscript/sendmail.false exists ( -z ), then don't send the mail.

---

