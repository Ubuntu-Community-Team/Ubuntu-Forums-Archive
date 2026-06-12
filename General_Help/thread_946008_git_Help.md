---
title: "git Help"
date: 2008-10-12
forum: General Help
---

### Post by davek20 on 2008-10-12
Hey guys. I'm having some problems with "git". My friend was helping me get everything set up but I still cannot get a clone of the repository. He gave me these links to work with:

[http://github.com/guides/providing-your-ssh-key#linux](http://github.com/guides/providing-your-ssh-key#linux)
[http://github.com/guides/addressing-authentication-problems-with-ssh](http://github.com/guides/addressing-authentication-problems-with-ssh)

Here is what I did:

First, went to the ~/.ssh folder and ran "ssh-keygen -t rsa", chose the filename, and a passphrase. 

Then I went to the site and put in the key (made sure there were no newline characters) The site is assembla.com if anyone has used it.

Then I ran "git config --global user.name "My Name"" and "git config user.email [email]myemail@example.com[/email]"

Then I ran "git clone [email]git@git.assembla.com[/email]: project.git" and it asked for my password, so I typed it in and it said it was the wrong password. So I tried the passphrase from the ssh-keygen, and still the wrong password. So I typed it slower and made sure it was correct, and still wrong (after 3 failed attempts it stops).

So I ran the command again and it didn't ask for my password but gave this:
```

Initialized empty Git repository in /home/dave/project/.git/
ssh_exchange_identification: Connection closed by remote host
fatal: The remote end hung up unexpectedly
fetch-pack from 'git@git.assembla.com:project.git' failed.

```

So after that, I made a config file from [http://github.com/guides/addressing-authentication-problems-with-ssh](http://github.com/guides/addressing-authentication-problems-with-ssh) but with the host and hostname changed and it still fails with the same output.

I have regenerated my keys several times, each with different passphrases and filenames and its still the same thing. Does anyone have some ideas on what is wrong and how to fix it?

---

### Post by Régis B. on 2009-01-05
Hi,
I am facing precisely the same problem, also on Assembla. Any idea on how to solve this?

---

