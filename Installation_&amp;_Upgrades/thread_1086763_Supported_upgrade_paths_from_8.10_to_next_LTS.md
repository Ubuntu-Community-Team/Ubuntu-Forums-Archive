---
title: "Supported upgrade paths from 8.10 to next LTS?"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by netJackDaw on 2009-03-04
If I remember correctly the only upgrade path supported from 6.10 to 8.04 LTS was via 7.04->7.10->8.04 LTS. There seems to be some reason behind this although it would have been nice to have 6.10 -> 8.04 LTS directly.

Now the setting in Software Sources (System->Administration->Software Sources) on the Updates tab for release upgrades, suggests (hints or whatever) that an upgrade from 8.10 to supposed next LTS 10.04 is directly supported. The options are to show new distribution releases for normal or LTS only.

Since I have both clients and servers running 8.10 it would be nice to know if an upgrade from 8.10->10.04 will be supported. If it is I am happy to wait for the next LTS at least on the server. If it is not I can upgrade to normal releases along the way since I will be forced to do it anyway when the next LTS is released.

Is there an answer to this question or are you just speculating like me?

---

### Post by zvacet on 2009-03-05
Normally you have to upgrade from one version to next.Things changed were becomes possible to upgrade from one **LTS** to another** LTS**.Now we have to options:

1.upgrade to every new coming release

2. install **LTS** and then wait for next** LTS **and upgrade.

That is why you have choice in synaptic.If you have an LTS installed and you don´t want to upgrade to every release witch comes next you will choose LTS.That way you will not get messages for version upgrades if they are not LTS.

---

### Post by netJackDaw on 2009-03-06
I suppose I am looking for consistency in the user interfaces. Since 8.10 is not an LTS and I still have the option in "Software Sources" to follow LTS only. What will happen if i choose that option? If I am not able to follow LTS only the option should not be there for non-LTS versions.

---

### Post by zvacet on 2009-03-06
> I still have the option in "Software Sources" to follow LTS only. What will happen if i choose that option?

When Jaunty become available you will not see that in update manager,because you choose to upgrade only LTS releases.Bad thing is that in that case you will skip releases and upgrade from 8.10 > 10.04 (I believe that will be next LTS) and result will be bad.If I remember corectlly option to upgrade is possible since Hardy,because that was first time we had two LTS.In short,if you want to upgrade via net to the next release select **normal release** option.

---

### Post by netJackDaw on 2009-03-09
In short: a tip to developers and maintainers! Keep the interface clean and avoid having options available that has the possibility of messing up peoples systems.

---

