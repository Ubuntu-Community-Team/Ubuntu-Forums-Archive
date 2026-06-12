---
title: "Error When Using setfacl"
date: 2008-09-12
forum: General Help
---

### Post by igfud on 2008-09-12
Hello,

My school has a lab with just Ubuntu machines.  Users are allowed to create a website on the school server, if they enter the following into the terminal:

> mkdir ~/public_html
setfacl -m u:apache:rx ~
setfacl -m u:apache:rx ~/public_html
setfacl -m d:u:apache:rx ~/public_html
I logged in remotely to the system using ssh, and discovered that I already happened to have a public_html folder in my home folder, so I skipped onto step two.  Each time I try to run the second step, I get the following error:

> setfacl: Option -m: Invalid argument near character 3
I skipped onto the third and fourth steps, but receive similar errors.  I even tried deleting my public_html directory and creating a new one, but that didn't help either.  Finally I physically came to the computer lab and tried all the above steps.  I received the same errors.

If I understand the commands correctly, I am essentially creating a directory called public_html.  Then I am allowing the "user" apache to read and write to this folder (I assume I'm just giving Apache Webserver access to my files).

Just to test, I tried using the setfacl command to give other students read and write access to my files, substituting apache with their usernames off the names of their home folders.  This worked fine.  For some reason does the user apache not exist or is not visible so I'm unable to give it access?

I tried accessing what would be my site (lab URL/~user_name).  I get a 403 Forbidden error, although I am able to find other users that have a site which is up and running.  Any idea on how I might be able to fix this?

Thanks,
igfud

---

### Post by Mister.Vash on 2008-09-13
From what I saw on my system, the error occurs when you don't have a matching user account or you have the wrong case in the name of the account.

You could ask the owner of the machines what the exact account name is and uid of it, or if these are lab servers that you are allowed to poke around on you can do the following.  Use your best judgement as to to what is appropriate use of the machine and ask the admin if you are not sure

```
awk -F: '{print $1}' /etc/passwd
```
Will list all the accounts on the server.  The is to check for an account called apache - since apache didn't seem to work for you, it might be named Apache, or it might be something else entirely.  If it does turn out to be Apache, run the following:
```
setfacl -m u:Apache:rx ~/public_html
```

If you still have trouble with the name, you could try the user id of the account instead of the name.  Run the following ( replace username with the name of the account you are checking )
```
id username
```
to get the uid.  Once you have it, run the following (replacing 1002 with the actual user ID ) 
```
setfacl -m u:1002:rx ~/public_html
```

---

