window.onerror=function(){};function EzPaq()
{this.content_hash="";this.content_orig="";this.leave_alone=false;this.global_window_props=Object.getOwnPropertyNames(window);this.find_new_entries=function(){var current_prop_list=Object.getOwnPropertyNames(window);var self=this;function find_duplicate(prop_name){return self.global_window_props.indexOf(prop_name)===-1;}
return current_prop_list.filter(find_duplicate);}
this.get_content=function(){var content="";if(document.head){content+=document.head.outerHTML;}
if(document.body){content+=document.body.outerHTML;if(ezpaq.leave_alone!=true)
{}}
this.content_orig=content;}
this.get_content_hash=function(){this.get_content();return window.md5(this.content_orig);}
this.get_cors=function(method,url){var xmlhttp;if(window.XMLHttpRequest){xmlhttp=new XMLHttpRequest();if(typeof xmlhttp.withCredentials!="undefined"){xmlhttp.open("GET",url,true);}else if(typeof XDomainRequest!="undefined"){xmlhttp=new XDomainRequest();xmlhttp.open("GET",url);}}else{xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");xmlhttp.open("GET",url);}
try
{xmlhttp.withCredentials=true;}
catch(err)
{}
return xmlhttp;}
this.load_page=function(){var url;if(document.location.href.indexOf('localhost')>-1)
{url="http://localhost:8080/middleton/content.php?ezjsu=http://deempleo.net/";}
else
{var uproto="http:";if(document.location.protocol=="https:"){uproto=document.location.protocol;}
url=uproto+"//g.ezoic.net?ezjsu="+encodeURIComponent(document.location.href);}
var xmlhttp=this.get_cors("POST",url);var self=this;xmlhttp.onreadystatechange=function(){if(xmlhttp.readyState==4){if(xmlhttp.status==200){var content=xmlhttp.responseText;if(content=='off')
{{ezpaq.unhide_page();ezpaq.leave_alone=true;}}
else
{var new_entries=self.find_new_entries();for(var i=0;i<new_entries.length;i++)
{try{delete window[new_entries[i]];}catch(e){}}
document.open();document.write(content);document.close();ezpaq.unhide_page();}}
else if(xmlhttp==400){ezpaq.unhide_page();}
else{{ezpaq.unhide_page();ezpaq.leave_alone=true;}}
ezpaq.sync_cookies();}}
xmlhttp.send();}
this.unhide_page=function(){if(typeof ezoTempStyle!='undefined')
{try
{document.getElementsByTagName('head')[0].removeChild(ezoTempStyle);}
catch(err){}}}
this.cookie_exp=function(cname)
{switch(cname){case"ezoawesome":return(365*2);break;case"ezouid":return(365*2);break;default:return 2;}}
this.is_ezoic=function(){return true;}
this.ezdomain=null;this.get_ez_domain=function(){if(this.ezdomain==null){if(typeof ezdomain!=='undefined'){this.ezdomain=ezdomain;}else{var i=document.evaluate("//script[contains(text(), 'ezdomain')]",document.documentElement);var e=i.iterateNext();if(e){var m=e.innerHTML.match(/ezdomain\s*=\s*['"]([^'"]*)['"]\s*;/);if(m){this.ezdomain=m[1];}}
if(this.ezdomain==null){this.ezdomain='';}}}
return this.ezdomain;}
this.set_cookie=function(cname,cvalue,exhours){var d=new Date();d.setTime(d.getTime()+(exhours*60*60*1000));var expires="expires="+d.toGMTString();var c=cname+"="+cvalue+"; "+expires+"; path=/";if(this.get_ez_domain()!=''){c=c+"; domain=."+ezdomain;}
document.cookie=c;}
this.sync_cookies=function(){var xmlhttp;var uproto="http:";if(document.location.protocol=="https:"){uproto=document.location.protocol;}
var url=uproto+"//g.ezoic.net/ezoic/gc.php";xmlhttp=this.get_cors("GET",url);xmlhttp.onreadystatechange=function(){if(xmlhttp.readyState==4){if(xmlhttp.status==200){json_cookies=xmlhttp.responseText;ez_cookies=JSON.parse(json_cookies);for(var key in ez_cookies)
{if(typeof ez_cookies[key]=="undefined")
{val="";}
else
{val=ez_cookies[key];}
ezpaq.set_cookie(key,val,ezpaq.cookie_exp(key));}}}}
xmlhttp.send();}
this.DoWork=function(){this.load_page();}}
try
{if(typeof ezpaq=="undefined")
{css='';if(document.addEventListener){css='body{display:none}';}
var ezoTempStyle=document.createElement('style');ezoTempStyle.setAttribute('type','text/css');if(ezoTempStyle.styleSheet&&!ezoTempStyle.sheet)ezoTempStyle.styleSheet.cssText=css;else ezoTempStyle.appendChild(document.createTextNode(css));document.getElementsByTagName('head')[0].appendChild(ezoTempStyle);var ezpaq=new EzPaq();ezpaq.DoWork();var readyStateCheckInterval=setInterval(function(){if(document.readyState==="complete"){clearInterval(readyStateCheckInterval);if(ezpaq.leave_alone!=true)
{ezpaq.get_content();}
else
{ezpaq.unhide_page();}}},10);}}
catch(err){}
