---
title: "Freevo Headlines Plugin Problem"
date: 2008-07-30
forum: General Help
---

### Post by zdunham on 2008-07-30
Hii, I've recently just installed Freevo on the newest version of Ubuntu. Freevo itself starts up and works. I activated the headlines plugin in local_conf.py and have tried a lot of different RSS feeds, ones from the tested list that comes with Freevo and my own, and I get the same problem for all of them. I know my syntax must be right because the names and website links show up properly in Freevo, when I hit one of them in the terminal window it says: 

```

ERROR: could not open <whatever site>

```

This happens no matter what site I put in. Any ideas? Help would be appreciated, thanks in advance for any.

---

### Post by frenchn00b on 2009-12-15
> **zdunham said:**
> Hii, I've recently just installed Freevo on the newest version of Ubuntu. Freevo itself starts up and works. I activated the headlines plugin in local_conf.py and have tried a lot of different RSS feeds, ones from the tested list that comes with Freevo and my own, and I get the same problem for all of them. I know my syntax must be right because the names and website links show up properly in Freevo, when I hit one of them in the terminal window it says: 

```

ERROR: could not open <whatever site>

```

This happens no matter what site I put in. Any ideas? Help would be appreciated, thanks in advance for any.
  

[http://doc.freevo.org/GeneralPlugins/Newsheadlines](http://doc.freevo.org/GeneralPlugins/Newsheadlines)

> A plugin to list headlines from an XML (RSS) feed. To activate, put the following lines in local_conf.py:

plugin.activate('headlines', level=45)
HEADLINES_LOCATIONS = [ ("Advogato", "http://advogato.org/rss/articles.xml"),
 ("Dictionary.com Word of the Day", "http://www.dictionary.com/wordoftheday/wotd.rss"),
 ("DVD Review", "http://www.dvdreview.com/rss/newschannel.rss") ]

You will find the news entry in the main menu.

For a full list of tested sites, see "Docs/plugins/headlines.txt". 

---

