---
title: "[SOLVED] Firefox, how to change the search localization?"
date: 2008-09-11
forum: General Help
---

### Post by Local.tosh on 2008-09-11
Anyone know how i can change the search bar to display international google search results ([http://www.google.com/intl/en/](http://www.google.com/intl/en/)) instead of local ([http://www.google.nl/](http://www.google.nl/)) search results in firefox 3? 

My native language is English and this is so annoying :(

---

### Post by kokkus on 2008-09-11
I don't think that is possible. Google search is intergrated in firefox. If u need another search engine on your browser u should try epiphany or galaxy browser.

---

### Post by other guy on 2008-09-11
I hope you didn't give up. There is a way to change up the search selection in Firefox.
I myself have google.com/linux as an extra. I can switch between that and regular google.

[http://mycroft.mozdev.org/](http://mycroft.mozdev.org/)

If you need help using it. I will help. If I do not reply fast. Please send me a PM. Sicne the notify feature can sometimes not be fast. The page is straight forward though and easy to use.

Once you got the extra engines in. All you have to do is manage the engines. Then you can remove or add more if you like.

---

### Post by lovinglinux on 2008-09-11
Type [www.google.com](www.google.com) in the address bar. Then hit "Preferences" in the page, not in Firefox. You can change the languages for your searches there, but you must allow Google to save cookies on your machine.

---

### Post by Kangarooo on 2009-05-21
I did it and.. its not what i need..
maybe someone has answer on this question?
after changing preferences and putting my search preffered language still results are comming from some.. INTerantionl google results..
when i search with ctrl+k in search box then google page also has option search within latvian pages.. just like i need it..

ok here is example at first..
ctrl+L i write kangarooo and it showed
[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=kangarooo](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=kangarooo)
ctrl+K i write kangarooo and it showed all i need..
[http://www.google.lv/search?q=kangarooo&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.lv/search?q=kangarooo&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)
then in ctrl+L results i changed prefferences to search in latvian and its searching in 
[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=kangarooo](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=kangarooo)
then in ctrl+L results i changed prefferences to google BE in latvian and its searching in 
[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=kangarooo](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=kangarooo)
then in ctrl+L results i changed prefferences to google BE in latvian and Preffer search in Latvian its searching in 
[http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=kangarooo](http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=kangarooo)
when i seach in [http://www.google.com/intl/lv/](http://www.google.com/intl/lv/)
[http://www.google.com/search?hl=lv&q=kangarooo&btnG=Google+mekl%C4%93%C5%A1ana&lr=lang_lv&aq=f&oq=](http://www.google.com/search?hl=lv&q=kangarooo&btnG=Google+mekl%C4%93%C5%A1ana&lr=lang_lv&aq=f&oq=)


But i need with CTRL+L to work like CTRL+K is now working

Maybe we can also make better Ubuntu FF startPage and configuration preferences.. ;)


Here is also code of FF Ubuntu Home default page.. [HTML]chrome://ubufox/content/startpage.html[/HTML]
```
<html>
<head>
<title></title>

<script><!--

var HOMEPAGE_ONLINE = "http://start.ubuntu.com/9.04/";
var HOMEPAGE_OFFLINE = "file:///usr/share/ubuntu-artwork/home/index.html"
var HOMEPAGE_OFFLINE_TMPL = "/usr/share/ubuntu-artwork/home/locales/index-"

var prefs = Components.classes["@mozilla.org/preferences-service;1"]
           .getService(Components.interfaces.nsIPrefBranch);
var userAgentLocale = null;
try {
  var userAgentLocaleLocalized = null;

  try {
    userAgentLocaleLocalized = prefs.getComplexValue("general.useragent.locale",
                                                     Components.interfaces.nsIPrefLocalizedString);
  } catch (e) {}

  if (userAgentLocaleLocalized) {
      userAgentLocale = userAgentLocaleLocalized.toString();
  } else {
      userAgentLocale = prefs.getCharPref("general.useragent.locale");
  }
} catch (e) { userAgentLocale = "en-US";}

function get_valid_offlinehomepage() {
   var canonicalLangCode = userAgentLocale.replace("-","_");

   var preferredHomepage = HOMEPAGE_OFFLINE_TMPL + canonicalLangCode + ".html";

   var file = Components.classes['@mozilla.org/file/local;1']
              .createInstance(Components.interfaces.nsILocalFile);

   file.initWithPath(preferredHomepage);

   if (!file.exists())
     return HOMEPAGE_OFFLINE;
   return "file://"+preferredHomepage;
}

function getwebsite_async() {
  var req = new XMLHttpRequest();
  setTimeout("window.location=\""+get_valid_offlinehomepage()+"\"", 4000);
  req.open('HEAD', HOMEPAGE_ONLINE, true);
  req.onreadystatechange = function (aEvt) {

    if (req.readyState > 1) {
      if(req.status == 200)
       window.location=HOMEPAGE_ONLINE;
      else
       window.location=get_valid_offlinehomepage();
    }
  };
  req.send(null); 
}
--></script>

</head>
<body onload="getwebsite_async()">
</body>
</html>

```

And here is SearchBox google preferences.. fomr [HTML]file:///usr/lib/firefox-addons/searchplugins/google.xml[/HTML]
```
<SearchPlugin xmlns="http://www.mozilla.org/2006/browser/search/">
<ShortName>Google</ShortName>
<Description>Google Search</Description>
<InputEncoding>UTF-8</InputEncoding>
<Image width="16" height="16">data:image/x-icon;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAIAAACQkWg2AAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAaRJREFUeNpiVIg5JRURw0A0YAHio943kYV%2B%2Ff33%2BdvvX7%2F%2FMjEx8nKycrGzwKXOiPKzICvdeezLhCV3jp15%2Bfv%2FX0YGhv8MDDxMX2qKTIw0RK10eYD6QYqATvoPBkt3f5K0W9Ew4fjTFz%2F%2Bw8Dm3W8UPeZxqFa%2BevsFyD0twgfVsOfkRxHrtfV9u5BVQ8Crd98%2FffkGYQM1QJ20%2FfSPv79eNxQGYfpSVJADmcvEAHbr7oOX2dj%2FERNKIA2%2F%2F%2Fz%2FxfCDhYVoDUDw5P6vf9%2B5iY0HVmZGQWm%2BN3fff%2Fn2k4eLHS739x%2FDiRs%2Ff%2F%2F5x8HO%2FOHzN3djfqgNjIwMgc6qzLx%2Fpy47j2zY%2Feff06tXhOUucgxeun33AUZGpHh4%2Bvo7t8EyIJqz%2FhpasD59%2B5dNrqdnznZIsEL9ICXCsWuBCwvTv%2FymS5PWPP32ExEALz%2F%2BB5r848cPCJcRaMP9xaYQzofPPzfuvrnj0Jst%2B5%2F8%2Bc4sLPeDkYlRgJc93VPE18NIXkYUmJYQSQMZ%2FP3379uPH7%2F%2F%2FEETBzqJ0WqLGvFpe2LCC4AAAwAyjg7ENzDDWAAAAABJRU5ErkJggg%3D%3D</Image>
<Url type="application/x-suggestions+json" method="GET" template="http://suggestqueries.google.com/complete/search?output=firefox&amp;client=firefox&amp;hl={moz:locale}&amp;q={searchTerms}"/>
<Url type="text/html" method="GET" template="http://www.google.com/search">
  <Param name="q" value="{searchTerms}"/>
  <Param name="ie" value="utf-8"/>
  <Param name="oe" value="utf-8"/>

  <Param name="aq" value="t"/>
  <!-- Dynamic parameters -->
  <Param name="rls" value="{moz:distributionID}:{moz:locale}:{moz:official}"/>
  <MozParam name="client" condition="defaultEngine" trueValue="firefox-a" falseValue="firefox"/>
</Url>
<SearchForm>http://www.google.com/firefox</SearchForm>
</SearchPlugin>

```

---

