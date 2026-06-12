---
title: "Emulating sendmail for local website development"
date: 2008-11-11
forum: General Help
---

### Post by PaulWhipp on 2008-11-11
I'm using Ubuntu 8.10 to develop websites with lampp installed as my local test environment.

Everything works fine until I have tests that involve my local site trying to send mail.

Its a local development machine so postfix, sendmail or exim4 would be drastic overkill (and I tried configuring them unsuccessfully, probably because what I'm trying to do is below their radar).

So I hit on the 'bright' idea of emulating sendmail using a bash script and putting that into the php.ini file. Sadly that does not work either even though it seems fine from the command line (nothing gets written to the log file).

Does anyone know how to get php mail calls (etc.) to work in a local Ubuntu test environment? I don't care if they are sent to another mail server as real mail or simply recorded in a logfile for me to check.

---

### Post by PaulWhipp on 2008-11-11
To clarify - my sendmail emulation works fine but when installed as the php sendmail it reports no arguments and no body data in the log (the timestamp is there so I know it gets called at the same time that the mail call in php is invoked).

---

### Post by aaronp on 2008-11-11
I haven't tried this but you could just set up a gmail account and use the gmail smtp server to send mail back to yourself (or anyone really)

I think there is a function in php called PEAR that allows you to use a different smtp server than the server you are developing on

I am looking to try this at some point but haven't researched it yet.

hope this helps
Aaron

---

### Post by PaulWhipp on 2008-11-11
Thanks for the suggestion Aaron.

I've looked into that but can't find anything that would work the way I need it to. The code I'm writing is being deployed at a site where sendmail is working fine and I don't want to alter the existing code so that its different in the development versus deployment environments for obvious reasons.

---

### Post by aaronp on 2008-11-11
that's fair enough. sorry i couldn't help.
you could try looking into ssmtp which is apparently a pretty simple way to set up.

can you set up a simple pop server on your local machine? i'm just taking stabs in the dark now so not sure if this is at all possible

---

### Post by PaulWhipp on 2008-11-11
googling I found
[http://ubuntuland.nireblog.com/post/2008/04/19/ssmtp-a-simple-alternative-to-sendmail](http://ubuntuland.nireblog.com/post/2008/04/19/ssmtp-a-simple-alternative-to-sendmail)

sSMTP looks just the ticket -

installs fine with synaptic

[http://www.destr0yr.com/article.php/Gmail_and_sSMTP](http://www.destr0yr.com/article.php/Gmail_and_sSMTP)

has instructions for setting it up with gmail and they work except for the test. In 8.10 ubuntu on my system there is no mail command. To test the system at the command line use something like:

echo "some test text" | sendmail [email]someone@test.com[/email]

The problem is that, although the message is sent (a step forwards), it arrives with no content - the subject and body are blank.

Furthermore, the mail call in php now returns true but does not actually send the email so its not much cop for testing. All the permissions check out fine on the files.

So close... and yet.

---

