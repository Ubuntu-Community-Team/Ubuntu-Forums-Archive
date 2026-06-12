---
title: "I cannot delete a file in my trash!"
date: 2008-08-27
forum: General Help
---

### Post by Roman10 on 2008-08-27
[[IMG]http://img34.picoodle.com/data/img34/3/8/26/t_1m_6598741.png[/img]](http://www.picoodle.com/view.php?img=/3/8/26/f_1m_6598741.png&srv=img34)

[[IMG]http://img32.picoodle.com/data/img32/3/8/26/t_2m_727ebd5.png[/img]](http://www.picoodle.com/view.php?img=/3/8/26/f_2m_727ebd5.png&srv=img32)

[[IMG]http://img34.picoodle.com/data/img34/3/8/26/t_3m_2437c12.png[/img]](http://www.picoodle.com/view.php?img=/3/8/26/f_3m_2437c12.png&srv=img34)

[[IMG]http://img32.picoodle.com/data/img32/3/8/26/t_4m_3402db4.png[/img]](http://www.picoodle.com/view.php?img=/3/8/26/f_4m_3402db4.png&srv=img32)

Why? How can I delete it?

Thanks a lot

---

### Post by jerome1232 on 2008-08-27
It might be owned by root or read only or some such. Try it like this.

```
sudo rm -rvIf ~/.local/share/Trash
```

Now mind this is a very, very powerful command, what it does is give you root privilages (god of the system) removes all arguments recusivly (descends into subdirectories) and forces their deletion no matter what.

So as you can imagine a misstype can wipe a system, completely, so I added a few fail safes, -v means at least you know what is being deleted, -I asks you once if you are sure you want to do this, double check your command then you can say yes.

---

### Post by Roman10 on 2008-08-27
> **jerome1232 said:**
> It might be owned by root or read only or some such. Try it like this.

```
sudo rm -rvIf ~/.local/share/Trash
```

Now mind this is a very, very powerful command, what it does is give you root privilages (god of the system) removes all arguments recusivly (descends into subdirectories) and forces their deletion no matter what.

So as you can imagine a misstype can wipe a system, completely, so I added a few fail safes, -v means at least you know what is being deleted, -I asks you once if you are sure you want to do this, double check your command then you can say yes.

Thank you!

---

