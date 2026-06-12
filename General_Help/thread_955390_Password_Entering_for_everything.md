---
title: "Password Entering for everything"
date: 2008-10-22
forum: General Help
---

### Post by saintryan on 2008-10-22
Hello.

Noob question incomming: How do i make my ubuntu not ask me for my password every time i want to do something eg. access synaptic manager, enter sudo commands in terminal etc?
I'm already logged in so.. why ask?

thanks

---

### Post by Tanker Bob on 2008-10-22
This is an important security measure in Linux and should not be compromised. It keeps arbitrary and/or malicious code from being run on your computer without your permission. Such code can turn your computer into a mindless "bot" to be used by spammers and other unsavory characters. New users from other, less secure operating systems are not used to seeing this level of protection.

---

### Post by oldos2er on 2008-10-22
> **saintryan said:**
> Hello.

Noob question incomming: How do i make my ubuntu not ask me for my password every time i want to do something eg. access synaptic manager, enter sudo commands in terminal etc?
I'm already logged in so.. why ask?

thanks

 You're logged in as a user, but any changes to your system, e.g. installing or removing software requires admin privileges.

---

### Post by bodhi.zazen on 2008-10-22
> **saintryan said:**
> Hello.

Noob question incomming: How do i make my ubuntu not ask me for my password every time i want to do something eg. access synaptic manager, enter sudo commands in terminal etc?
I'm already logged in so.. why ask?

thanks

The proper way is to use either sudo -i or gksu

[uhelp]community/RootSudo[/uhelp]

You may circumvent this if you wish, but this is not supported on these forums.

Use a google search if you must.

These forums will help you learn sudo.

I am going to close this thread now as your original question has been answered and recently people like to post things on these threads they should not.

If you have questions about sudo or gksu please start a new thread and we will help.

---

