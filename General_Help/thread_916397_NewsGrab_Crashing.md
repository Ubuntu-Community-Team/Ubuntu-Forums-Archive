---
title: "NewsGrab Crashing"
date: 2008-09-10
forum: General Help
---

### Post by springerja on 2008-09-10
When I attempt to run an rss feed into newsgrab (gDesklet) I get this error message and it does not let me look at any of the articles, and after a while, crashes all of my desklets (clock, calender). Any ideas on how to fix it?

'NoneType' object is not callable                                                    
/home/alex/.gdesklets/Displays/NewsGrab/newsgrab.script                              
  589                                   Dsp.time[i].value = item[i + pos][3]         
  590                                                                                
  591           refresh_arrows()                                                     
  592                                                                                
  593           if news.refresh == 1:                                                
> 594                   news.refresh = 0                                             
  595                   if wrap != width:                                            
  596                           set_wrap(width)                                      
  597                                                                                
  598                   update_actions()                                             
  599                   refresh_newsitems()                                          
  600

---

