---
title: "how to search for words and then change them with bash?"
date: 2008-11-24
forum: General Help
---

### Post by jakonj on 2008-11-24
Another bash problem. Im familiar with bash but at this moment i dont now what to do for my new problem. What i want:
1. Script should search the file *.story* (whitch is html file) to find **<code></code>** tags
2. When the script finds <code> tags it should search for words inside those <code> tags
3. There will be some kind of archive for words (can i use something like:
```
base-words="if|fi|then|else|[0-9]"
```
?)
4. Script should find those words **under** <code> tags and change them (practical example:
In words base i have the word "then" and "echo". When script finds those words it will change "then" and "echo" to **"<span class="echo">echo</span>"** and **"<span class="then">then</span>"**).

What i need this for? Well im editing bashblogger and i added *code* style under CSS but i would like to change colors for some well known commands (like if, then, echo, else, goto, read, ""...). That way i could write nice and good formated scripts on my blog with nice colors (syntax highlight is great thing).

Is there any way to do this?

p.s. I know that there are some robust js-s for this but i would like to add this as default option in my edited bashblogger so i can use only nano to write .story and nothing else.

---

