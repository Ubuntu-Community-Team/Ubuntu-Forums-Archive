---
title: "Need suggestions for an employee attendance system"
date: 2008-09-30
forum: General Help
---

### Post by Warakurna on 2008-09-30
I need a **web based** system that does the following:

- Shows an overall calendar of which of my employees are out of the office and why
- Allows users to have their own calendars to track attendance
- Allows users to submit applications to their supervisors for vacation time
- Tracks birthdays!
- Has different levels of access (employee, supervisor, HR, admin, etc)
- Allows users to quickly and easily fill out forms for sick days to their supervisors
- Tracks comp time if possible
- Authenticates against LDAP (and hopefully AD)
- Prefer PHP/MySQL
- Does not look stupid

I run a few LAMP servers in the office and I can manage such a system fairly easily provided there is such a system.

This is my first post on the Ubuntu forums and I thank you very much for your consideration.

---

### Post by nsche on 2008-09-30
You might find some useful apps on [www.opensourcerails.com](www.opensourcerails.com).  They are in Ruby on Rails.  I don't think any of them are exactly what you want but you can get them and change them to do what you want.  I thought rubytime there might be a partial match.  Also go to rubyforge.org and take a look through the projects there to see if there might be a match.  All of these suggestions are ruby suggestions but I think you would find Ruby on Rails to be an easier way to meet your objectives than php possibly.  Hosting would be about the same and ROR is web browser and database oriented.

Good luck
Norm

---

### Post by Warakurna on 2008-09-30
I have been using Drupal for years now.  I have considered it as an option but I was hoping that there was a system out there to do these things already that I simply had not come across yet.  I have been scouring sourceforge and freshmeat but there don't seem to be tools that handle more than half of these options at any one given time.

I may have to settle for an LDAP authenticating web calendar that handles various levels of permissions and hope I can figure out something for supervisor approval of vacation/sick time.

Thyme seems like my best option at the moment.

[http://www.extrosoft.com/]("http://www.extrosoft.com/")

---

### Post by dprichard on 2008-10-29
Here is one we developed.  We looked all over and couldn't find one so we developed it from scratch.  It has a calendar overview, lets you setup multiple approval levels, lets employees submit requests and email managers for approval.  It has all the features you are looking for.

[PHP Employee Attendance Tracking]("http://www.dsolutionsgroup.com/employee-attendance-tracking.php")

---

