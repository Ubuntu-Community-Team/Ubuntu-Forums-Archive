---
title: "Bizarre ignoring after trying to hibernate"
date: 2008-06-14
forum: Hardware
---

### Post by Avuton Olrich on 2008-06-14
The GUIs refuse to hibernate if I click to (if I click the plug and 'hibernate' or if I click the log out then hibernate). The screen immediately blanks and asks for a password like it went through the whole process already. Checking the logs it says 'User suspended' then a second later 'User resumed'. This is on 2.6.24-16 (anything later breaks hibernate for me).

Executing '# sudo /etc/acpi/hibernate.sh' works perfectly(!).

Thanks!

---

