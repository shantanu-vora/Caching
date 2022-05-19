# **Caching & Cache Replacement Mechanisms**

## **Abstract**

Web caching is one of the most common techniques for increasing the performance speed of web applications by placing data files that are more likely to be revisited closer to the user. This paper describes and reviews what is web caching and summarizes the common caching approaches.

## **Introduction**

Web Caching can be implemented on 3 different levels - Client level, Proxy level, and original server level. Cache replacement is the core idea behind achieving efficient caching. Hence, it is pertinent to come up with efficient cache replacement algorithms. Now the problem with traditional caching policies is that some popular web objects are requested frequently while a large set of web objects are lying around unrequested in the cache memory and blocking cache space. This is known as the Cache Pollution problem. It is therefore difficult to identify such factors that can influence the cache replacement process. There is however another technique called Web Prefetching which when integrated with web caching can improve end-user experienced latency by 60% but it is beyond the scope of this review paper. 


### **Caching**

1. Caching means storing data files in a temporary storage location closer to you which lets you access them faster the next time you request them. The idea behind caching is basically to improve user experience by storing data files in a temporary location that is closer to the user. Consider the scenario where a user wants to visit a web application and enters the URL of that application. Every search for a URL is an HTTP request to some server requesting the contents of a particular website. That website may contain HTML files, Javascript files, or multimedia such as videos, images, text, etc. So every time the user visits that website, a ton of data and multimedia files have to be fetched and loaded from the remote server and the browser renders that data. This fetching and loading of a large amount of data can result in latency and performance issues thus resulting in a poor user experience. 

2. So the first time a user visits a website, some of this data is stored locally on his computer by the browser in the form of cache memory. When the user visits the website next time, those files will be loaded directly from the local cache instead of fetching and loading them from the server. This results in faster loading of web pages. However, on the flip side, it also risks confidential or sensitive information of users being exposed to cybercriminals. Caching data could result in authentication information or browsing history being exposed if a browser is left unattended.

### **Basic types of Web cache**

1. **Browser Cache**: Browser cache is located in the client. There are cache settings on all modern browsers like Chrome and Firefox from which users can see the cached data. The browser cache mostly comes into effect when the user clicks on the back or forward button to revisit previously requested pages. In this case, the browser immediately servers the cached web objects stored in the browser cache instead of making an HTTP request.

2. **Proxy Server Cache**: It works similarly to the browser cache except that the browser cache serves cache to a single user whereas the proxy server serves cache to multiple users. Whenever a user requests any web object, the proxy server stores it on a decentralized cache database. After that, if another user requests that same web object then the proxy server first checks in the cache database, if it is available or not. If the requested web object is found in the cached database then the proxy server sends it to the user. If it has expired then the proxy server will request the origin server and send it back to the user. 

3. **CDN Caching**: A CDN is a network of proxy servers. It incorporates proxy servers to achieve caching. Normally when you open a website your request has to travel to the server where the web pages are located. It fetches these pages and returns them to you. It's totally fine when the distance between you and the server is less but when the server is located at the other end of the globe, it may take a while for the page to load. This means people closer to the server can access the server faster while the people away from it will have a lower page speed. To fix this, we have something called CDN, meaning a Content Delivery Network. This means we have a network of servers around the world and the original file is cached on each of these servers. If a site is using CDN, it will be accessible at the same speed to everyone irrespective of where they are looking at it geographically. For example, Youtube has its content delivery network, that's why it's fast for all of us. Netflix also uses CDN and it uses an algorithm to push the most viewed shows. That's why popular shows load faster while others load slower.

4. **Origin Server Cache**: To decrease the load on the server, the origin server also employs a server-side cache just like how the browser does.

### **Web Caching algorithms**

Because the cache size is limited, to determine what will be stored and what will be evicted a replacement policy is needed to be employed. Some of the important factors influencing the decision making of these policies include:- 

1. Recency
2. Frequency
3. Size
4. Cost of accessing the object
5. Access latency

Based on these factors following approaches can be implemented:-

1. Least Recently Used (LRU algorithm): As the name suggests, it chooses the least recently accessed web object to replace and create space for the newly requested object. It is the simplest approach to implement. It can be considered a recency-based approach but it does not consider the size or the access latency of the objects.

2. Least Frequently Used (LFU algorithm): This is a frequency bases approach where the object which is requested more number of times or rather the more popular objects are kept in the cache while the less popular objects are evicted to make room for newly requested objects. But this approach suffers from the cache pollution problem.

3. Size: Size is also a common factor in determining replacement objects. This approach evicts the largest objects to accommodate newly requested objects. This approach leads to the cache area being filled with a large number of small-sized web objects. Because this approach only considers the size, the smaller-sized objects may never be requested again.


## **Conclusion**
Web caching is a proven method to improve performance and scalability. However, the conventional approaches have some downsides to them. They focus on a single factor in making decisions as to what should be replaced with what. A hybrid caching approach can be designed which incorporates all factors and optimally influences the replacement policy. Further intelligent caching mechanisms can be developed with help of a neural net.


## **References**

* [Tufts University CS Department Presentation](https://www.cs.tufts.edu/comp/117/slides/performance.pdf)
* [Catchpoint blog on Web Caching](https://www.catchpoint.com/blog/web-caching)
* [Managewp.com blog on Types of Web Cache](https://managewp.com/blog/types-of-web-cache)
* [Fortinet.com](https://www.fortinet.com/resources/cyberglossary/what-is-caching)
* [Cloudflare's article on Caching](https://www.cloudflare.com/en-in/learning/cdn/what-is-caching/)
* [Utkarsh Manipal's blog post on Caching Techniques](https://bootcamp.uxdesign.cc/caching-techniques-one-should-know-603e09d2b298)