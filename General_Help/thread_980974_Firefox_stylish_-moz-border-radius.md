---
title: "Firefox stylish: -moz-border-radius"
date: 2008-11-13
forum: General Help
---

### Post by ChrisBookwood on 2008-11-13
Hi,

I have been trying to add rounded corners[1] to the tabs in Firefix with the Stylish extension, but it doesn't seem to be working, though all the comments I can't find on the internet about those types of styles, are positive.

Am I the only one with that problem, it is something generel not working on ubuntu or what?


[1] [http://userstyles.org/styles/8624](http://userstyles.org/styles/8624)


Regards,
Chris Bookwood

---

### Post by ChrisBookwood on 2008-11-14
Anybody?

---

### Post by ChrisBookwood on 2008-11-14
I've made these two mockups [1][2] - the first one being the one I believe is possible without too much configuration, and the second being how I would like firefox to work with tabs, if I could choose with no limit.

Hope you guys get the idéa, and maybe come up with another way to achieve it, if not a clue to fix the Stylish problem.

[1] [http://dl.getdropbox.com/u/168187/firefoxmockup_001.jpg](http://dl.getdropbox.com/u/168187/firefoxmockup_001.jpg)
[2] [http://dl.getdropbox.com/u/168187/firefoxmockup_002.jpg](http://dl.getdropbox.com/u/168187/firefoxmockup_002.jpg)


Regards,
Chris Bookwood

---

### Post by ChrisBookwood on 2008-11-14
Okay, I've have now succeded in changing the roundness of the tabs. I did that by adding '-moz-appearance' set to none on the tab-element.

I have made the following css, and the first draft is almost done. I still need to get rid of the dark strip above active tabs as showed in [2].

Here's the css code to make tabs look like on [2]:
[html]@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

toolbar {
  -moz-appearance : none !important;
  border-bottom : 1px solid #9a9690 !important;
}

.tabbrowser-strip {
  background-color : #d5d1cd !important;
}

.tabbrowser-strip:not([on]) .tabs-bottom  {
  -moz-box-sizing: border-box !important;
  display: none !important;
}

.tabbrowser-tabs > tab {
  -moz-appearance: none !important;
  
  border-left: 2px solid !important;
  border-bottom: 2px solid !important;
  border-right: 2px solid !important;
  -moz-border-left-colors: threedshadow #c2bcb7 !important;
  -moz-border-bottom-colors: threedshadow #c2bcb7 !important;
  -moz-border-right-colors: threedshadow #c2bcb7 !important;
  -moz-border-radius-bottomleft: 7px !important;
  -moz-border-radius-bottomright: 7px !important;
  -moz-box-sizing: border-box !important;

  margin : -1px 1px 2px 1px !important;
  background-color : #b8b3ad !important;
}

.tabbrowser-tabs > tab[selected="false"] {
  margin-bottom : 4px !important;
  background-color : #cac7c0 !important;
  -moz-border-left-colors: threedshadow #d3d0c9 !important;
  -moz-border-bottom-colors: threedshadow #d3d0c9 !important;
  -moz-border-right-colors: threedshadow #d3d0c9 !important;
  -moz-opacity: 0.7 !important;
}[/html]And on [1], you can see the current css in use.

[1] [http://dl.getdropbox.com/u/168187/almost.jpg](http://dl.getdropbox.com/u/168187/almost.jpg)
[2] [http://dl.getdropbox.com/u/168187/firefoxmockup_002.jpg](http://dl.getdropbox.com/u/168187/firefoxmockup_002.jpg)


Regards,
Chris Bookwood

---

### Post by ChrisBookwood on 2008-11-16
There must be someone who can help me? I'm completely blank...

---

### Post by ulzy on 2009-04-11
[http://www.youtube.com/watch?v=W2VIVlnfMBg](http://www.youtube.com/watch?v=W2VIVlnfMBg)

It works!

---

