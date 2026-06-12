---
title: "[SOLVED] MySQL: Auto-insert date"
date: 2008-10-21
forum: General Help
---

### Post by x1a4 on 2008-10-21
Hi,

I want the `date` field of a table to be automatically filled with the current date whenever I add data.  For example, when I do: 
```

insert into 
     `news` (`id`, `date`, `news`) 
     values ('','','Something that's happened');

```
`id` will be set automatically because I have set auto_increment.  I want the same for `date` only that the current date should be inserted with the following format: 'DD MM/YY'

How do I do it?  

Thank you.

---

### Post by Paul41 on 2008-10-21
This should help.

[http://dev.mysql.com/doc/refman/5.0/en/date-and-time-functions.html#function_now](http://dev.mysql.com/doc/refman/5.0/en/date-and-time-functions.html#function_now)

---

### Post by Paul41 on 2008-10-21
I was thinking about your question and this may be more what you are looking for.

[http://dev.mysql.com/doc/refman/5.0/en/timestamp.html](http://dev.mysql.com/doc/refman/5.0/en/timestamp.html)

---

### Post by x1a4 on 2008-10-21
Thanks Paul41.  TIMESTAMP did the trick.  I modified the table like so
```

alter table `news` 
     change `date` `date` timestamp 
     on update current_timestamp not null 
     default current_timestamp

```
and it did the trick.

---

