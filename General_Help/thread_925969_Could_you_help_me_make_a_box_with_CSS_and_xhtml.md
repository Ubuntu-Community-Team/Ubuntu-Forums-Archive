---
title: "Could you help me make a box with CSS and xhtml ?"
date: 2008-09-21
forum: General Help
---

### Post by Sycron on 2008-09-21
I wish to make a CSS box and I don't know how to achieve this. Any help is appreciated. The pics hope helps you what I mean.

---

### Post by FakeOutdoorsman on 2008-09-21
For Mozilla and Safari users you can use CSS3:
> .roundedbox {
	-moz-border-radius: 5px;
	-webkit-border-radius: 5px;
	border: 3px solid white;
	background: gray;
}

---

### Post by Sycron on 2008-09-21
Since my first design template was very hard to export as xhtml and very sluggish because of very much alpha channels I decided to start again but VERY VERY lightweight.

So I'm going to use your tip, thank you. It works.

---

### Post by Sycron on 2008-09-24
Hey, why it's not valid CSS :( ? I get ```
15  	 div.box_border  	 Property -moz-border-radius doesn't exist :  16px
15 	div.box_border 	Property -webkit-border-radius doesn't exist : 16px 
```

:( Please help me. And thank you so much. It's so nice to have that round borders.

---

### Post by FakeOutdoorsman on 2008-09-24
border-radius is a CSS 3 property, but I'm not sure if any browsers support border-radius yet.  Firefox doesn't seem to.  It doesn't exist in CSS 2.1, which is the default of the W3C CSS validator. -moz-border-radius, -webkit-border-radius, and -khtml-border-radius are browser layout engine specific and are to be used until CSS 3 gets adopted by the browsers.  I wouldn't be concerned with the validation errors related to -*-border-radius.

---

### Post by Sycron on 2008-09-24
I tried to validate CSS 2.1 and 3 but neither of them works. I will have a footer on my site in which I say Valid xhtml and valid CSS ... It's a good idea to hide Valid CSS ?

---

### Post by FakeOutdoorsman on 2008-09-24
Having invalid CSS or XHTML isn't always a bad thing and does not mean your site is "wrong".  Sometimes the standards are behind the technology.  I try to make my sites valid, but I don't follow it like a rule.  I mostly use it as tool for error checking.
It is your choice if you want to include the validation statements in the footer.

---

### Post by Sycron on 2008-09-25
I will include them :). Thanks for this good advice.

---

