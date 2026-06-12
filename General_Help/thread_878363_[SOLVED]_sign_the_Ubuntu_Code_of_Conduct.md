---
title: "[SOLVED] sign the Ubuntu Code of Conduct"
date: 2008-08-02
forum: General Help
---

### Post by perlluver on 2008-08-02
Anyone know how to sign the Ubuntu Code of Conduct?  I have my key, I download the file, I follow what is listed on launchpad, and yet it will not let me upload the file, it says it has no Public key.

---

### Post by overdrank on 2008-08-02
Moved to General Help :)

---

### Post by spiderbatdad on 2008-08-02
somehow you are not adding your key correctly to the file. Try copying it from the terminal and pasting it into the file.

---

### Post by p_quarles on 2008-08-02
What procedure are you using for signing the document? If nothing else, you can use the gpg command line tool to ensure that you do this part correctly.

---

### Post by perlluver on 2008-08-02
> **p_quarles said:**
> What procedure are you using for signing the document? If nothing else, you can use the gpg command line tool to ensure that you do this part correctly.

I am using gpg --clearsign the document name.

---

### Post by drs305 on 2008-08-02
> **perlluver said:**
> I am using gpg --clearsign the document name.

Do you have more than one key? Did you make a key specifically for this registration? If you have more than one key, it might be trying to use the wrong one. If you think this might be the case, try this:

Open up ~/.gnupg/gpg.conf

Find the lines that look like this, and uncomment the key you are trying to use. Comment any other keys listed:
```

# If you have more than 1 secret key in your keyring, you may want to
# uncomment the following option and set your preferred keyid. Sae the file after making the changes.

#default-key 621CC
default-key 5B1DC
```

Try running the commands again.

---

### Post by spiderbatdad on 2008-08-02
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

see the section about launchpad. You have to add your fingerprint, then decrypt the email sent to you. Also make sure you have added your key to the ubuntu keyserver...its all in the wiki.

I remember struggling with it for most of an afternoon before finally getting it. I've only done it once, so it's not that fresh in my mind, how to do it. I just followed the wiki.

---

### Post by perlluver on 2008-08-02
> **spiderbatdad said:**
> [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

see the section about launchpad. You have to add your fingerprint, then decrypt the email sent to you. Also make sure you have added your key to the ubuntu keyserver...its all in the wiki.

I remember struggling with it for most of an afternoon before finally getting it. I've only done it once, so it's not that fresh in my mind, how to do it. I just followed the wiki.

I did all of this, the problem is when trying to upload to the server it says no public key.  I have signed it, already have the key.

---

### Post by spiderbatdad on 2008-08-02
you're using the command gpg --clearsign UbuntuCodeofConduct-1.0.1.txt?

As I said I remember having the same problem for a while. It had to do with where the key was getting placed in the document by clearsign. I think I ended up running gpg --list-keys and pasting it in myself. Something is getting left out by clearsign...you'll get it. It just takes some persistence.

or do you mean problem uploading to ubuntu keyserver?

---

### Post by perlluver on 2008-08-02
> **spiderbatdad said:**
> you're using the command gpg --clearsign UbuntuCodeofConduct-1.0.1.txt?

As I said I remember having the same problem for a while. It had to do with where the key was getting placed in the document by clearsign. I think I ended up running gpg --list-keys and pasting it in myself. Something is getting left out by clearsign...you'll get it. It just takes some persistence.

or do you mean problem uploading to ubuntu keyserver?

Yeah I am having a problem with the gpg --clearsign.  What did you paste into the document?

---

### Post by spiderbatdad on 2008-08-02
If i remember correctly...the .asc containing the entire fingerprint...to the top of the document.

---

### Post by perlluver on 2008-08-02
> **spiderbatdad said:**
> If i remember correctly...the .asc containing the entire fingerprint...to the top of the document.

That is what I paste in there, but it says no Public key.  It has GPG and checksum SHA1 and there is a lot of info below, but Ubuntu will not decode it, it says there is no Info.

[CODE]-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

= Ubuntu Code of Conduct =

This Code of Conduct covers your behaviour as a member of the Ubuntu
Community, in any forum, mailing list, wiki, web site, IRC channel,
install-fest, public meeting or private correspondence. The Ubuntu
Community Council will arbitrate in any dispute over the conduct of a
member of the community.

      '''Be considerate.''' Your work will be used by other people,
      and you in turn will depend on the work of others. Any decision
      you take will affect users and colleagues, and we expect you to
      take those consequences into account when making decisions. For
      example, when we are in a feature freeze, please don't upload
      dramatically new versions of critical system software, as other
      people will be testing the frozen system and will not be
      expecting big changes.

      '''Be respectful.''' The Ubuntu community and its members treat
      one another with respect. Everyone can make a valuable
      contribution to Ubuntu. We may not always agree, but
      disagreement is no excuse for poor behaviour and poor
      manners. We might all experience some frustration now and then,
      but we cannot allow that frustration to turn into a personal
      attack. It's important to remember that a community where people
      feel uncomfortable or threatened is not a productive one. We
      expect members of the Ubuntu community to be respectful when
      dealing with other contributors as well as with people outside
      the Ubuntu project and with users of Ubuntu.

      '''Be collaborative.''' Ubuntu and Free Software are about
      collaboration and working together. Collaboration reduces
      redundancy of work done in the Free Software world, and improves
      the quality of the software produced. You should aim to
      collaborate with other Ubuntu maintainers, as well as with the
      upstream community that is interested in the work you do. Your
      work should be done transparently and patches from Ubuntu should
      be given back to the community when they are made, not just when
      the distribution releases. If you wish to work on new code for
      existing upstream projects, at least keep those projects
      informed of your ideas and progress. It may not be possible to
      get consensus from upstream or even from your colleagues about
      the correct implementation of an idea, so don't feel obliged to
      have that agreement before you begin, but at least keep the
      outside world informed of your work, and publish your work in a
      way that allows outsiders to test, discuss and contribute to
      your efforts.

      '''When you disagree,''' consult others. Disagreements, both
      political and technical, happen all the time and the Ubuntu
      community is no exception. The important goal is not to avoid
      disagreements or differing views but to resolve them
      constructively. You should turn to the community and to the
      community process to seek advice and to resolve
      disagreements. We have the Technical Board and the Community
      Council, both of which will help to decide the right course for
      Ubuntu. There are also several Project Teams and Team Leaders,
      who may be able to help you figure out which direction will be
      most acceptable. If you really want to go a different way, then
      we encourage you to make a derivative distribution or
      alternative set of packages available using the Ubuntu Package
      Management framework, so that the community can try out your
      changes and ideas for itself and contribute to the discussion.

      '''When you are unsure,''' ask for help. Nobody knows
      everything, and nobody is expected to be perfect in the Ubuntu
      community (except of course the SABDFL). Asking questions avoids
      many problems down the road, and so questions are
      encouraged. Those who are asked should be responsive and
      helpful. However, when asking a question, care must be taken to
      do so in an appropriate forum. Off-topic questions, such as
      requests for help on a development mailing list, detract from
      productive discussion.

      '''Step down considerately.''' Developers on every project come
      and go and Ubuntu is no different. When you leave or disengage
      from the project, in whole or in part, we ask that you do so in
      a way that minimises disruption to the project. This means you
      should tell people you are leaving and take the proper steps to
      ensure that others can pick up where you leave off.
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQFIlLrhIW6IvO5HfAMRAlzCAJ47x+Q6onu+7p9GA6ZOyXNoagAZtQCeM2zk
2TzJndyBLR+nT96xrwy6KIM=
=QQWs
-----END PGP SIGNATURE-----{[CODE]

---

### Post by drs305 on 2008-08-02
You've done the pasting correctly because it has your pgp code at the bottom. I suspect they don't have your public key.


If there is no public key, you probably need to do 2 things:
```

pub   1024D/**12345678** 2007-01-26
      Key fingerprint = 0464 39CD 2486 190A 2C5A  0739 0E68 04DC 16E7 CB72
uid                  Matthew Revell (My test OpenPGP key) <test@matthewrevelltest.com>
sub   2048g/ABCDEF12 2007-01-26

```

Send the key to ubuntu:
```
gpg --send-keys --keyserver keyserver.ubuntu.com **12345678**
```

Paste the fingerprint in the launchpad box. 
Generate the fingerprint:
```
gpg --fingerprint
```

Go to Launchpad and paste it in:
[https://launchpad.net/people/+me/+editpgpkeys]("https://launchpad.net/people/+me/+editpgpkeys")

Paste in the fingerprint:
```
0464 39CD 2486 190A 2C5A  0739 0E68 04DC 16E7 CB72

```

Then try sending it again.

---

### Post by Dr Small on 2008-08-02
Did you ever add and verify your GPG key with Launchpad?
*Dr Small waves at drs305. :)

---

### Post by perlluver on 2008-08-02
> **drs305 said:**
> You've done the pasting correctly because it has your pgp code at the bottom. I suspect they don't have your public key.


If there is no public key, you probably need to do 2 things:
```

pub   1024D/**12345678** 2007-01-26
      Key fingerprint = 0464 39CD 2486 190A 2C5A  0739 0E68 04DC 16E7 CB72
uid                  Matthew Revell (My test OpenPGP key) <test@matthewrevelltest.com>
sub   2048g/ABCDEF12 2007-01-26

```

Send the key to ubuntu:
```
gpg --send-keys --keyserver keyserver.ubuntu.com **12345678**
```

Paste the fingerprint in the launchpad box. 
Generate the fingerprint:
```
gpg --fingerprint
```

Go to Launchpad and paste it in:
[https://launchpad.net/people/+me/+editpgpkeys]("https://launchpad.net/people/+me/+editpgpkeys")

Paste in the fingerprint:
```
0464 39CD 2486 190A 2C5A  0739 0E68 04DC 16E7 CB72

```

Then try sending it again.

This is what I got from launchpad.  The key D3DDFB2661FD25B6F175957E6EDFEB4CFE4F6BCF has already been imported.

---

### Post by jimv on 2008-08-03
Just curious, why would one sign the Ubuntu Code of Conduct?

---

### Post by p_quarles on 2008-08-03
> **jimv said:**
> Just curious, why would one sign the Ubuntu Code of Conduct?
It's required in order to become an Ubuntu Member.

---

### Post by perlluver on 2008-08-03
Got it solved, set my default key in the seahorse file.

Thank you everybody.

---

### Post by jimv on 2008-08-03
> **p_quarles said:**
> It's required in order to become an Ubuntu Member.

What's an Ubuntu member?

---

### Post by spiderbatdad on 2008-08-03
> **jimv said:**
> What's an Ubuntu member?

Someone who has signed the Code of Conduct.:)

There is a little more:[http://www.ubuntu.com/community/processes/newmember](http://www.ubuntu.com/community/processes/newmember)

---

