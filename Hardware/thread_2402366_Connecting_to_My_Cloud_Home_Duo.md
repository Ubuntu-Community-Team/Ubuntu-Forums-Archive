---
title: "Connecting to My Cloud Home Duo"
date: 2018-09-29
forum: Hardware
---

### Post by jeremiekilt on 2018-09-29
[COLOR=#004B78][FONT=Helvetica]I’m trying to connect to My Cloud Home Duo from my PC, with Ubuntu 18.04.[/FONT][/COLOR]
[COLOR=#004B78][FONT=Helvetica]I open Nautilus and find easily My Cloud.[/FONT][/COLOR]
[COLOR=#004B78][FONT=Helvetica]I click on My Cloud. A window open, inviting me to enter my username and password.

[IMG]https://discourse-cdn-sjc1.com/wd/uploads/default/original/3X/5/8/589be8b203b98149acc7fb25c5dd3c0b30532362.png[/IMG]

I enter my username and password, but then I have this error message: “An invalid username was provided”
[IMG]https://discourse-cdn-sjc1.com/wd/uploads/default/original/3X/a/8/a83c25bcf4a54ad1a662ff8b5617db2ec0fe68db.png[/IMG]

Is there a way to access the private user space of the My Cloud Home Duo on Ubuntu?[/FONT][/COLOR]

---

### Post by TheFu on 2018-09-29
Don't usernames need to be 7-bit ASCII to work?

Localhost is the computer you are on, which probably isn't the MyCloud device.

BTW, [https://www.theinquirer.net/inquirer/news/3005875/hackers-find-85-vulnerabilities-in-wd-my-cloud-range](https://www.theinquirer.net/inquirer/news/3005875/hackers-find-85-vulnerabilities-in-wd-my-cloud-range) - be very careful using that device. I wouldn't allow access using any WD internet services even if you are fully patched today.  

All the other internet storage devices like this have had similar issues.  Treat all of them as LAN-only storage and use other tools like openvpn or sftp to connect in from the internet, if that is a need.

[https://www.oreilly.com/library/view/practical-unix-and/0596003234/ch04s01.html](https://www.oreilly.com/library/view/practical-unix-and/0596003234/ch04s01.html) is a little old school, but ... 
> Some versions of Unix have problems with usernames that do not start with a lowercase letter or that contain special characters such as punctuation or control characters. Usernames containing certain unusual characters will also cause problems for various application programs, including some network mail programs. For this reason, many sites allow only usernames that contain lowercase letters and numbers and further require that all usernames start with a letter.
I wouldn't worry about the 8 character limit. That hasn't been an issue for 30+ yrs, but using UTF8 characters probably isn't ok yet for all versions, especially for a WD My Cloud device.

But I'm just guessing.

---

