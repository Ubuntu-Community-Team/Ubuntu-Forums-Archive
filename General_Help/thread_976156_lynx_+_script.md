---
title: "lynx + script"
date: 2008-11-09
forum: General Help
---

### Post by yousillygoose on 2008-11-09
Hello.  I am working on a script and need a bit of help.  I have a script that uses lynx to monitor a forum.  When a new post is made on the forum I have my script make a sound through my pc beep, my speakers, and I also have the script send an email to myself (I know, a super alert system).  I do all of this so that I can be the first person to respond to the forum (there will be 50 responses within 2 minutes and it is helpful to be the first one).  

I would love to be able to automate this script to also post a reply for me.  I was wondering if you all knew of a way to make my script post a reply.  I am going to change the website in the script address so that I can keep a bit of anonymity.  Here is how the script looks so far:


> while : ; do
   if lynx -dump [http://website.xxxxxxxx](http://website.xxxxxxxx) |grep "\]0 [0-20]" ; then
      echo t
      echo | mailx -s "NEW THREAD, go post" [email]myemail@gmail.com[/email] & tput bel & beep -l 1500
   fi
   sleep 2s
   date
done


What this script does is check the website for a new thread made with 0 replies and only 0-20 views.  It then sends the mail and the noises.  If it finds no new threads it simply prints the date.  When it finds a new thread it posts:

 >                                   [39]0 1
t

in the terminal showing that the new thread has 0 replies and 1 view.  I don't really know what the [39] means here.  I would like to have the script take it one step further and autoreply to this exact thread that it finds.  Is this possible?  Let me know.

yousillygoose

---

### Post by yousillygoose on 2008-11-09
I still need help :)

---

