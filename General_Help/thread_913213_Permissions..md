---
title: "Permissions."
date: 2008-09-07
forum: General Help
---

### Post by enderal on 2008-09-07
I wrecked ubuntu not long ago messing with permissions and want to avoid it again. I chmoded something in the etc directory and it created a gigantic mess.

I'm going to be working in Apache folders and such. For example I want all permissions in the www directory.

I've tried things in Users and Groups to no avail. I can find no concrete answer.


Thank you.

---

### Post by mike2357 on 2008-09-07
I'm not sure exactly what your question is, but I make it a rule to not tinker with permissions in /var, /usr, /etc, /bin, /sbin or /lib, nor do I add, delete or change any files there.  The only exceptions are changing a configuration file in /etc (after making a backup), or doing stuff in /usr/local.  Other than that, I use my home directory.

Incidentally, PATH variables are generally set to /usr/local/bin before /usr, /sbin and /bin.  Therefore, if you want to compile something from source that's already installed from Ubuntu, you put your compiled version in /usr/local/bin, and that version will get called first.  Also, if you create a mess of something you've put in /usr/local (which unfortunately I've done more than once), you can delete it with significantly less risk of bringing your system to its knees, since the original files in /usr, /bin, etc. from Ubuntu are untouched.

If I haven't addressed your question, post back and I'll give it another shot.

---

### Post by enderal on 2008-09-07
Thanks mike2357

I need to edit, rename, add files and directories in the www directory for web pages and such. I also need to work with apache files and things.

I can do all that with the command line but that is a hassle.

I created a file in my home directory and tried to move it into the www directory but it will not allow that.

I need a quick way to do it. Do I need to FTP it all in? Can you FTP into your own computer?

I know what you mean about messing with permissions and want to avoid that as totally as possible.

Thanks again

---

### Post by jerome1232 on 2008-09-07
Why not make a directive in apache for say /home/youruserhere/public_html

And put the webpages there. That way you do your editing where it's supposed to be.

[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/) gives an example of how to tell apache where you want to store your website,

---

### Post by enderal on 2008-09-07
Wow! Thank you! That was very good help. Everything seems to be up and running now.

Thanks again.:)

---

### Post by timjamz on 2008-10-08
Great advice for newbies like me!  "Thank you" from me also.

---

