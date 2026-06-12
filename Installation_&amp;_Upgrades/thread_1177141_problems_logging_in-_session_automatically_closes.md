---
title: "problems logging in- session automatically closes"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by qui8 on 2009-06-03
i am using ubuntu 9.04 for a month or so on my dell inspiron 6000 after my windows was crashing. all of a sudden, when today i started my comp, i am getting this message after logging in immediately i am logged out with the message saying 

"your session only lasted less than 10 seconds. if you have not logged out yourself this could mean that there is some installation problem or that you may be out of disk space. try logging in with one of the failsafe sessions to see if you can fix this problem."

with checkbox saying (view details (~/xsession - errors file)

when i check the box, it further shows following details:

/etc/gdm/xsession : beginning session set up.....
home/me/.profile: 1 : syntax error : new line unexpected

after logging in with failsafe mode, i checked out the files xsession and also .profile. i felt the problem  as shown was in .profile file, so i am posting the same here:

 </metadata>
    </info>
  </bookmark>
  <bookmark href="file:///home/me/.mozilla/firefox/profiles.ini" added="2009-05-29T03:40:49Z" modified="2009-05-29T03:40:51Z" visited="2009-05-29T03:40:49Z">
    <info>
      <metadata owner="http://freedesktop.org">
        <mime:mime-type type="text/plain"/>
        <bookmark:groups>
          <bookmark:group>gedit</bookmark:group>
        </bookmark:groups>
        <bookmark:applications>
          <bookmark:application name="File Manager" exec="&apos;gedit&apos;" modified="2009-05-29T03:40:49Z" count="1"/>
          <bookmark:application name="Text Editor" exec="&apos;gedit %u&apos;" modified="2009-05-29T03:40:51Z" count="1"

can anybody tell me what to do? i am continuing with the failsafe mode but is it fine or should i change things?

thanks.

---

