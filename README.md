# ViberBot

<div id="content" class="post-single-content box mark-links">
							<p>Chat Bot is very popular these days. With Chat Bot, you can connect to your customers with Deeper Interactions and grow your business.</p>
<p>In this post, I am going to share how to develop Viber Chat Bot in 6 simple steps using PHP.</p>
<h3>1. Create Public Account in Viber</h3>
<p>To get started, first of all, you should have a Viber Public account. If you don’t have a Public Account, apply for a Public Account in Viber <a href="https://www.viber.com/en/public-accounts" target="_blank" rel="noopener"> Public Accounts</a> page.<br>
Once your application has been approved, you will be sent a invitation message to start creating your Public Account. To create account, you need to:<br>
• Restart your device.<br>
• Enter the Public Accounts home-screen. You will see the <em>Create Public Accounts</em> button.<br>
• Tap on the button, and get started!</p>
<h3>2. Get authentication token</h3>
<p>The authentication token is generated upon Public Account creation and can be viewed by the account’s admin in the “edit info” screen of Public Account.</p>
<p><strong>Example token</strong>: 455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8</p>
<figure id="attachment_166" style="max-width: 176px" class="wp-caption aligncenter"><noscript>&lt;IMG class="size-medium wp-image-166 " alt="Viber edit account detail" width="176" height="300" data-sizes="(max-width: 176px) 100vw, 176px" data-srcset="https://i2.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_account_edit_detail.png?resize=176%2C300 176w, https://i2.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_account_edit_detail.png?w=306 306w" data-src="https://i2.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_account_edit_detail.png?resize=176%2C300" src="https://i2.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_account_edit_detail.png?resize=176%2C300" data-recalc-dims="1"&gt;</noscript><img class="size-medium wp-image-166 lazyloaded" alt="Viber edit account detail" width="176" height="300" data-sizes="(max-width: 176px) 100vw, 176px" data-srcset="https://i2.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_account_edit_detail.png?resize=176%2C300 176w, https://i2.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_account_edit_detail.png?w=306 306w" data-src="http://thedebuggers.com/wp-content/uploads/2017/01/viber_account_edit_detail-176x300.png" sizes="(max-width: 176px) 100vw, 176px" srcset="https://i2.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_account_edit_detail.png?resize=176%2C300 176w, https://i2.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_account_edit_detail.png?w=306 306w" src="http://thedebuggers.com/wp-content/uploads/2017/01/viber_account_edit_detail-176x300.png"><figcaption class="wp-caption-text">Example for Viber edit account detail page</figcaption></figure><center>
<ins class="adsbygoogle" style="display:inline-block;width:336px;height:280px" data-ad-client="ca-pub-2649652639912551" data-ad-slot="3129945437" data-adsbygoogle-status="done"><ins id="aswift_2_expand" style="display:inline-table;border:none;height:280px;margin:0;padding:0;position:relative;visibility:visible;width:336px;background-color:transparent;"><ins id="aswift_2_anchor" style="display:block;border:none;height:280px;margin:0;padding:0;position:relative;visibility:visible;width:336px;background-color:transparent;"><iframe width="336" height="280" frameborder="0" marginwidth="0" marginheight="0" vspace="0" hspace="0" allowtransparency="true" scrolling="no" allowfullscreen="true" onload="var i=this.id,s=window.google_iframe_oncopy,H=s&amp;&amp;s.handlers,h=H&amp;&amp;H[i],w=this.contentWindow,d;try{d=w.document}catch(e){}if(h&amp;&amp;d&amp;&amp;(!d.body||!d.body.firstChild)){if(h.call){setTimeout(h,0)}else if(h.match){try{h=s.upd(h,i)}catch(e){}w.location.replace(h)}}" id="aswift_2" name="aswift_2" style="left:0;position:absolute;top:0;width:336px;height:280px;"></iframe></ins></ins></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script></center>
<h3>3. Setup webhook</h3>
<p>Once the token is received, you will be able to set your account’s <em>webhook</em>. This <em>webhook</em> will be used for receiving callbacks &amp; user messages from Viber.</p>
<p>Setting the webhook will be done by calling the <em>set_webhook</em> API with a valid &amp; certified URL.</p>
<p>Once a <em>set_webhook</em> request is sent, Viber will send a callback to the <em>webhook</em> to check its availability, and return a response to the user.</p>
<p><em><strong>Note</strong>: Before sending request to set_webhook API, we need to have code to handle callback from Viber at our webhook URL. Sample PHP Code is provided in this article.</em></p>
<p>Call a <strong>POST request</strong> to this api:<br>
https://chatapi.viber.com/pa/set_webhook<br>
Post Parameters:</p>
<pre class="EnlighterJSRAW" data-enlighter-language="json" style="display: none;">

```
{
  "auth_token": "455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8",
  "url": "https://mysite.com/webhook_page",
  "event_types": ["delivered", "seen"]
}

```
</pre><div class="EnlighterJSWrapper enlighterEnlighterJSWrapper"><ol class="hoverEnabled enlighterEnlighterJS EnlighterJS"><li class=" odd"><span class="br0">{</span><span class=""></span></li><li class=" even"><span class="">  </span><span class="kw1">"auth_token"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8"</span><span class="sy0">,</span><span class=""></span></li><li class=" odd"><span class="">  </span><span class="st0">"url"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"https://mysite.com/webhook_page"</span><span class="sy0">,</span><span class=""></span></li><li class=" even"><span class="">  </span><span class="kw1">"event_types"</span><span class="sy0">:</span><span class=""> </span><span class="br0">[</span><span class="st0">"delivered"</span><span class="sy0">,</span><span class=""> </span><span class="st0">"seen"</span><span class="br0">]</span><span class=""></span></li><li class=" odd"><span class=""></span><span class="br0">}</span></li></ol><pre style="display: none;">

```

{
  "auth_token": "455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8",
  "url": "https://mysite.com/webhook_page",
  "event_types": ["delivered", "seen"]
}


```
</pre><div class="EnlighterJSToolbar"><a class="EnlighterJSInfoButton" title="EnlighterJS Syntax Highlighter"></a><a class="EnlighterJSRawButton" title="Toggle RAW Code"></a><a class="EnlighterJSWindowButton" title="Open Code in new Window"></a><span class="clear"></span></div></div>
<p><em>auth_token</em> = The token string provided by Viber on PA creation.<br><em>url</em> = PA webhook URL to receive callbacks &amp; messages from users (must use SSL i.e. https)<br><em>event_type</em> = (optional) Indicates the types of Viber events that the PA owner would like to be notified about. Default values: [“delivered”, “seen”]</p>
<p>In order to make POST request to <em>set_webhook API</em>, we can use cURL or tools like POSTMAN. Here’s the sample PHP code:</p>
<pre class="EnlighterJSRAW" data-enlighter-language="php" style="display: none;">

```
<?php

$url = 'https://chatapi.viber.com/pa/set_webhook';

$jsonData='{ "auth_token": "your_auth_token", "url": "https://yoursite.com/webhook_page" }';

$ch = curl_init($url);
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS, $jsonData);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type: application/json'));
$result = curl_exec($ch);
curl_close($ch);

?>
	
```
</pre>

<div class="EnlighterJSWrapper enlighterEnlighterJSWrapper"><ol class="hoverEnabled enlighterEnlighterJS EnlighterJS"><li class=" odd"><span class="de1">&lt;?php</span><span class=""></span></li><li class=" even"><span class=""></span></li><li class=" odd"><span class=""></span><span class="kw3">$url</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="st1">'https://chatapi.viber.com/pa/set_webhook'</span><span class="">;</span></li><li class=" even"><span class=""></span></li><li class=" odd"><span class=""></span><span class="kw3">$jsonData</span><span class="sy0">=</span><span class="st1">'{ "auth_token": "your_auth_token", "url": "https://yoursite.com/webhook_page" }'</span><span class="">;</span></li><li class=" even"><span class=""></span></li><li class=" odd"><span class=""></span><span class="kw3">$ch</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="me0">curl_init</span><span class="br0">(</span><span class="kw3">$url</span><span class="br0">)</span><span class="">;</span></li><li class=" even"><span class=""></span><span class="me0">curl_setopt</span><span class="br0">(</span><span class="kw3">$ch</span><span class="">, </span><span class="kw4">CURLOPT_POST</span><span class="">, </span><span class="nu0">1</span><span class="br0">)</span><span class="">;</span></li><li class=" odd"><span class=""></span><span class="me0">curl_setopt</span><span class="br0">(</span><span class="kw3">$ch</span><span class="">, </span><span class="kw4">CURLOPT_POSTFIELDS</span><span class="">, </span><span class="kw3">$jsonData</span><span class="br0">)</span><span class="">;</span></li><li class=" even"><span class=""></span><span class="me0">curl_setopt</span><span class="br0">(</span><span class="kw3">$ch</span><span class="">, </span><span class="kw4">CURLOPT_HTTPHEADER</span><span class="">, </span><span class="me0">array</span><span class="br0">(</span><span class="st1">'Content-Type: application/json'</span><span class="br0">)</span><span class="br0">)</span><span class="">;</span></li><li class=" odd"><span class=""></span><span class="kw3">$result</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="me0">curl_exec</span><span class="br0">(</span><span class="kw3">$ch</span><span class="br0">)</span><span class="">;</span></li><li class=" even"><span class=""></span><span class="me0">curl_close</span><span class="br0">(</span><span class="kw3">$ch</span><span class="br0">)</span><span class="">;</span></li><li class=" odd"><span class=""></span></li><li class=" even"><span class=""></span><span class="de2">?&gt;</span></li></ol><pre style="display: none;">&lt;?php

$url = 'https://chatapi.viber.com/pa/set_webhook';

$jsonData='{ "auth_token": "your_auth_token", "url": "https://yoursite.com/webhook_page" }';

$ch = curl_init($url);
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS, $jsonData);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type: application/json'));
$result = curl_exec($ch);
curl_close($ch);

?&gt;</pre><div class="EnlighterJSToolbar"><a class="EnlighterJSInfoButton" title="EnlighterJS Syntax Highlighter"></a><a class="EnlighterJSRawButton" title="Toggle RAW Code"></a><a class="EnlighterJSWindowButton" title="Open Code in new Window"></a><span class="clear"></span></div></div>
<p>&nbsp;</p>
<p>After we call <em>set_webhook</em> api, Viber will send a callback to the <strong>webhook URL</strong> to confirm it is available, i.e https://mysite.com/webhook_page in the above example. The callback data format is as follow:</p>
<pre class="EnlighterJSRAW" data-enlighter-language="json" style="display: none;">{
  "event":"webhook",
  "timestamp":1457764197627,
  "message_token":4912661846655238145
}</pre><div class="EnlighterJSWrapper enlighterEnlighterJSWrapper"><ol class="hoverEnabled enlighterEnlighterJS EnlighterJS"><li class=" odd"><span class="br0">{</span><span class=""></span></li><li class=" even"><span class="">  </span><span class="kw1">"event"</span><span class="sy0">:</span><span class="st0">"webhook"</span><span class="sy0">,</span><span class=""></span></li><li class=" odd"><span class="">  </span><span class="st0">"timestamp"</span><span class="sy0">:</span><span class="nu0">1457764197627</span><span class="sy0">,</span><span class=""></span></li><li class=" even"><span class="">  </span><span class="kw1">"message_token"</span><span class="sy0">:</span><span class="nu0">4912661846655238145</span><span class=""></span></li><li class=" odd"><span class=""></span><span class="br0">}</span></li></ol><pre style="display: none;">{
  "event":"webhook",
  "timestamp":1457764197627,
  "message_token":4912661846655238145
}</pre><div class="EnlighterJSToolbar"><a class="EnlighterJSInfoButton" title="EnlighterJS Syntax Highlighter"></a><a class="EnlighterJSRawButton" title="Toggle RAW Code"></a><a class="EnlighterJSWindowButton" title="Open Code in new Window"></a><span class="clear"></span></div></div>
<p><em>event</em> = Callback type – which event triggered the callback. Possible value is webhook.<br><em>timestamp</em>= Time of the event that triggered the callback<br><em>message_token</em> = Unique ID of the message</p>
<p>Now we need to give response as</p>
<pre class="EnlighterJSRAW" data-enlighter-language="json" style="display: none;">{
  "status": 0,
  "status_message": "ok",
  "event_types": ["delivered", "seen"] //Not yet implemented
}</pre><div class="EnlighterJSWrapper enlighterEnlighterJSWrapper"><ol class="hoverEnabled enlighterEnlighterJS EnlighterJS"><li class=" odd"><span class="br0">{</span><span class=""></span></li><li class=" even"><span class="">  </span><span class="kw1">"status"</span><span class="sy0">:</span><span class=""> </span><span class="nu0">0</span><span class="sy0">,</span><span class=""></span></li><li class=" odd"><span class="">  </span><span class="st0">"status_message"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"ok"</span><span class="sy0">,</span><span class=""></span></li><li class=" even"><span class="">  </span><span class="kw1">"event_types"</span><span class="sy0">:</span><span class=""> </span><span class="br0">[</span><span class="st0">"delivered"</span><span class="sy0">,</span><span class=""> </span><span class="st0">"seen"</span><span class="br0">]</span><span class=""> //Not yet implemented</span></li><li class=" odd"><span class=""></span><span class="br0">}</span></li></ol><pre style="display: none;">{
  "status": 0,
  "status_message": "ok",
  "event_types": ["delivered", "seen"] //Not yet implemented
}</pre><div class="EnlighterJSToolbar"><a class="EnlighterJSInfoButton" title="EnlighterJS Syntax Highlighter"></a><a class="EnlighterJSRawButton" title="Toggle RAW Code"></a><a class="EnlighterJSWindowButton" title="Open Code in new Window"></a><span class="clear"></span></div></div>
<p><em>status</em> = Action result (0 for success, error number for errors)<br><em>status_message</em> = Ok or failure reason<br><em>event_types</em> = delivered or seen (not implemented yet)</p>
<p>This will set <em>webhook url</em>. Now, whenever an event occurs related to the Public Account, a callback is sent to the webhook url and we need to handle the events in webhook url that is discussed below.</p>
<p><strong>Code for webhook url:</strong></p>
<pre class="EnlighterJSRAW" data-enlighter-language="php" style="display: none;">&lt;?php 

$request = file_get_contents("php://input");
$input = json_decode($request, true);

if($input['event'] == 'webhook') {
  $webhook_response['status']=0;
  $webhook_response['status_message']="ok";
  $webhook_response['event_types']='delivered';
  echo json_encode($webhook_response);
  die;
}
else if($input['event'] == "subscribed") {
  // when a user subscribes to the public account
}
else if($input['event'] == "conversation_started"){
  // when a conversation is started
}
elseif($input['event'] == "message") {
  /* when a user message is received */
  $type = $input['message']['type']; //type of message received (text/picture)
  $text = $input['message']['text']; //actual message the user has sent
  $sender_id = $input['sender']['id']; //unique viber id of user who sent the message
  $sender_name = $input['sender']['name']; //name of the user who sent the message

  // here goes the data to send message back to the user
  $data['auth_token'] = "4453b6ac1s345678-e02c5f12174805f9-95f29ebc06af09a8";
  $data['receiver'] = $sender_id;
  $data['text'] = "The message to send to user";
  $data['type'] = 'text';

  //here goes the curl to send data to user
  $ch = curl_init("https://chatapi.viber.com/pa/send_message ");
  curl_setopt($ch, CURLOPT_POST, 1);
  curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data));
  curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type: application/json'));
  $result = curl_exec($ch);
}

?&gt;

</pre><div class="EnlighterJSWrapper enlighterEnlighterJSWrapper"><ol class="hoverEnabled enlighterEnlighterJS EnlighterJS"><li class=" odd"><span class="de1">&lt;?php</span><span class=""> </span></li><li class=" even"><span class=""></span></li><li class=" odd"><span class=""></span><span class="kw3">$request</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="me0">file_get_contents</span><span class="br0">(</span><span class="st0">"php://input"</span><span class="br0">)</span><span class="">;</span></li><li class=" even"><span class=""></span><span class="kw3">$input</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="me0">json_decode</span><span class="br0">(</span><span class="kw3">$request</span><span class="">, </span><span class="kw4">true</span><span class="br0">)</span><span class="">;</span></li><li class=" odd"><span class=""></span></li><li class=" even"><span class=""></span><span class="kw1">if</span><span class="br0">(</span><span class="kw3">$input</span><span class="br0">[</span><span class="st1">'event'</span><span class="br0">]</span><span class=""> </span><span class="sy0">=</span><span class="sy0">=</span><span class=""> </span><span class="st1">'webhook'</span><span class="br0">)</span><span class=""> </span><span class="br0">{</span><span class=""></span></li><li class=" odd"><span class="">  </span><span class="kw3">$webhook_response</span><span class="br0">[</span><span class="st1">'status'</span><span class="br0">]</span><span class="sy0">=</span><span class="nu0">0</span><span class="">;</span></li><li class=" even"><span class="">  </span><span class="kw3">$webhook_response</span><span class="br0">[</span><span class="st1">'status_message'</span><span class="br0">]</span><span class="sy0">=</span><span class="st0">"ok"</span><span class="">;</span></li><li class=" odd"><span class="">  </span><span class="kw3">$webhook_response</span><span class="br0">[</span><span class="st1">'event_types'</span><span class="br0">]</span><span class="sy0">=</span><span class="st1">'delivered'</span><span class="">;</span></li><li class=" even"><span class="">  </span><span class="kw1">echo</span><span class=""> </span><span class="me0">json_encode</span><span class="br0">(</span><span class="kw3">$webhook_response</span><span class="br0">)</span><span class="">;</span></li><li class=" odd"><span class="">  </span><span class="kw1">die</span><span class="">;</span></li><li class=" even"><span class=""></span><span class="br0">}</span><span class=""></span></li><li class=" odd"><span class=""></span><span class="kw1">else</span><span class=""> </span><span class="kw1">if</span><span class="br0">(</span><span class="kw3">$input</span><span class="br0">[</span><span class="st1">'event'</span><span class="br0">]</span><span class=""> </span><span class="sy0">=</span><span class="sy0">=</span><span class=""> </span><span class="st0">"subscribed"</span><span class="br0">)</span><span class=""> </span><span class="br0">{</span><span class=""></span></li><li class=" even"><span class=""> </span><span class="co1"> // when a user subscribes to the public account</span><span class=""></span></li><li class=" odd"><span class=""></span><span class="br0">}</span><span class=""></span></li><li class=" even"><span class=""></span><span class="kw1">else</span><span class=""> </span><span class="kw1">if</span><span class="br0">(</span><span class="kw3">$input</span><span class="br0">[</span><span class="st1">'event'</span><span class="br0">]</span><span class=""> </span><span class="sy0">=</span><span class="sy0">=</span><span class=""> </span><span class="st0">"conversation_started"</span><span class="br0">)</span><span class="br0">{</span><span class=""></span></li><li class=" odd"><span class=""> </span><span class="co1"> // when a conversation is started</span><span class=""></span></li><li class=" even"><span class=""></span><span class="br0">}</span><span class=""></span></li><li class=" odd"><span class=""></span><span class="me0">elseif</span><span class="br0">(</span><span class="kw3">$input</span><span class="br0">[</span><span class="st1">'event'</span><span class="br0">]</span><span class=""> </span><span class="sy0">=</span><span class="sy0">=</span><span class=""> </span><span class="st0">"message"</span><span class="br0">)</span><span class=""> </span><span class="br0">{</span><span class=""></span></li><li class=" even"><span class="">  </span><span class="co2">/* when a user message is received */</span><span class=""></span></li><li class=" odd"><span class="">  </span><span class="kw3">$type</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="kw3">$input</span><span class="br0">[</span><span class="st1">'message'</span><span class="br0">]</span><span class="br0">[</span><span class="st1">'type'</span><span class="br0">]</span><span class="">;</span><span class="co1"> //type of message received (text/picture)</span><span class=""></span></li><li class=" even"><span class="">  </span><span class="kw3">$text</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="kw3">$input</span><span class="br0">[</span><span class="st1">'message'</span><span class="br0">]</span><span class="br0">[</span><span class="st1">'text'</span><span class="br0">]</span><span class="">;</span><span class="co1"> //actual message the user has sent</span><span class=""></span></li><li class=" odd"><span class="">  </span><span class="kw3">$sender_id</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="kw3">$input</span><span class="br0">[</span><span class="st1">'sender'</span><span class="br0">]</span><span class="br0">[</span><span class="st1">'id'</span><span class="br0">]</span><span class="">;</span><span class="co1"> //unique viber id of user who sent the message</span><span class=""></span></li><li class=" even"><span class="">  </span><span class="kw3">$sender_name</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="kw3">$input</span><span class="br0">[</span><span class="st1">'sender'</span><span class="br0">]</span><span class="br0">[</span><span class="st1">'name'</span><span class="br0">]</span><span class="">;</span><span class="co1"> //name of the user who sent the message</span><span class=""></span></li><li class=" odd"><span class=""></span></li><li class=" even"><span class=""> </span><span class="co1"> // here goes the data to send message back to the user</span><span class=""></span></li><li class=" odd"><span class="">  </span><span class="kw3">$data</span><span class="br0">[</span><span class="st1">'auth_token'</span><span class="br0">]</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="st0">"4453b6ac1s345678-e02c5f12174805f9-95f29ebc06af09a8"</span><span class="">;</span></li><li class=" even"><span class="">  </span><span class="kw3">$data</span><span class="br0">[</span><span class="st1">'receiver'</span><span class="br0">]</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="kw3">$sender_id</span><span class="">;</span></li><li class=" odd"><span class="">  </span><span class="kw3">$data</span><span class="br0">[</span><span class="st1">'text'</span><span class="br0">]</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="st0">"The message to send to user"</span><span class="">;</span></li><li class=" even"><span class="">  </span><span class="kw3">$data</span><span class="br0">[</span><span class="st1">'type'</span><span class="br0">]</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="st1">'text'</span><span class="">;</span></li><li class=" odd"><span class=""></span></li><li class=" even"><span class=""> </span><span class="co1"> //here goes the curl to send data to user</span><span class=""></span></li><li class=" odd"><span class="">  </span><span class="kw3">$ch</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="me0">curl_init</span><span class="br0">(</span><span class="st0">"https://chatapi.viber.com/pa/send_message "</span><span class="br0">)</span><span class="">;</span></li><li class=" even"><span class="">  </span><span class="me0">curl_setopt</span><span class="br0">(</span><span class="kw3">$ch</span><span class="">, </span><span class="kw4">CURLOPT_POST</span><span class="">, </span><span class="nu0">1</span><span class="br0">)</span><span class="">;</span></li><li class=" odd"><span class="">  </span><span class="me0">curl_setopt</span><span class="br0">(</span><span class="kw3">$ch</span><span class="">, </span><span class="kw4">CURLOPT_POSTFIELDS</span><span class="">, </span><span class="me0">json_encode</span><span class="br0">(</span><span class="kw3">$data</span><span class="br0">)</span><span class="br0">)</span><span class="">;</span></li><li class=" even"><span class="">  </span><span class="me0">curl_setopt</span><span class="br0">(</span><span class="kw3">$ch</span><span class="">, </span><span class="kw4">CURLOPT_HTTPHEADER</span><span class="">, </span><span class="kw1">array</span><span class="br0">(</span><span class="st1">'Content-Type: application/json'</span><span class="br0">)</span><span class="br0">)</span><span class="">;</span></li><li class=" odd"><span class="">  </span><span class="kw3">$result</span><span class=""> </span><span class="sy0">=</span><span class=""> </span><span class="me0">curl_exec</span><span class="br0">(</span><span class="kw3">$ch</span><span class="br0">)</span><span class="">;</span></li><li class=" even"><span class=""></span><span class="br0">}</span><span class=""></span></li><li class=" odd"><span class=""></span></li><li class=" even"><span class=""></span><span class="de2">?&gt;</span></li></ol><pre style="display: none;">&lt;?php 

$request = file_get_contents("php://input");
$input = json_decode($request, true);

if($input['event'] == 'webhook') {
  $webhook_response['status']=0;
  $webhook_response['status_message']="ok";
  $webhook_response['event_types']='delivered';
  echo json_encode($webhook_response);
  die;
}
else if($input['event'] == "subscribed") {
  // when a user subscribes to the public account
}
else if($input['event'] == "conversation_started"){
  // when a conversation is started
}
elseif($input['event'] == "message") {
  /* when a user message is received */
  $type = $input['message']['type']; //type of message received (text/picture)
  $text = $input['message']['text']; //actual message the user has sent
  $sender_id = $input['sender']['id']; //unique viber id of user who sent the message
  $sender_name = $input['sender']['name']; //name of the user who sent the message

  // here goes the data to send message back to the user
  $data['auth_token'] = "4453b6ac1s345678-e02c5f12174805f9-95f29ebc06af09a8";
  $data['receiver'] = $sender_id;
  $data['text'] = "The message to send to user";
  $data['type'] = 'text';

  //here goes the curl to send data to user
  $ch = curl_init("https://chatapi.viber.com/pa/send_message ");
  curl_setopt($ch, CURLOPT_POST, 1);
  curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data));
  curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type: application/json'));
  $result = curl_exec($ch);
}

?&gt;</pre><div class="EnlighterJSToolbar"><a class="EnlighterJSInfoButton" title="EnlighterJS Syntax Highlighter"></a><a class="EnlighterJSRawButton" title="Toggle RAW Code"></a><a class="EnlighterJSWindowButton" title="Open Code in new Window"></a><span class="clear"></span></div></div>

<center>
<ins class="adsbygoogle" style="display:inline-block;width:336px;height:280px" data-ad-client="ca-pub-2649652639912551" data-ad-slot="3129945437" data-adsbygoogle-status="done"><ins id="aswift_3_expand" style="display:inline-table;border:none;height:280px;margin:0;padding:0;position:relative;visibility:visible;width:336px;background-color:transparent;"><ins id="aswift_3_anchor" style="display:block;border:none;height:280px;margin:0;padding:0;position:relative;visibility:visible;width:336px;background-color:transparent;"><iframe width="336" height="280" frameborder="0" marginwidth="0" marginheight="0" vspace="0" hspace="0" allowtransparency="true" scrolling="no" allowfullscreen="true" onload="var i=this.id,s=window.google_iframe_oncopy,H=s&amp;&amp;s.handlers,h=H&amp;&amp;H[i],w=this.contentWindow,d;try{d=w.document}catch(e){}if(h&amp;&amp;d&amp;&amp;(!d.body||!d.body.firstChild)){if(h.call){setTimeout(h,0)}else if(h.match){try{h=s.upd(h,i)}catch(e){}w.location.replace(h)}}" id="aswift_3" name="aswift_3" style="left:0;position:absolute;top:0;width:336px;height:280px;"></iframe></ins></ins></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script></center>
<h3>4. Receive message</h3>
<p>Whenever user sends a message to the public account in 1-to-1 chat, the following callback data is sent to the webhook url.</p>
<pre class="EnlighterJSRAW" data-enlighter-language="json" style="display: none;">{ 
  "event": "message", 
  "timestamp": 1457764197627, 
  "message_token": 4912661846655238145, 
  "sender": 
  { 
    "id": "01234567890A=",
     "name": "yarden",
     "avatar": "http://avatar_url"
   }, 
  "message": 
  { 
    "type": "text",
     "text": "a message to the service",
     "media": "http://download_url",
     "location":
    {
      "lat": 50.76891,
      "lon": 6.11499},
      "tracking_data": "tracking data"
     } 
  }
}</pre><div class="EnlighterJSWrapper enlighterEnlighterJSWrapper"><ol class="hoverEnabled enlighterEnlighterJS EnlighterJS"><li class=" odd"><span class="br0">{</span><span class=""> </span></li><li class=" even"><span class="">  </span><span class="kw1">"event"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"message"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">  </span><span class="st0">"timestamp"</span><span class="sy0">:</span><span class=""> </span><span class="nu0">1457764197627</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">  </span><span class="kw1">"message_token"</span><span class="sy0">:</span><span class=""> </span><span class="nu0">4912661846655238145</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">  </span><span class="kw1">"sender"</span><span class="sy0">:</span><span class=""> </span></li><li class=" even"><span class="">  </span><span class="br0">{</span><span class=""> </span></li><li class=" odd"><span class="">    </span><span class="kw1">"id"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"01234567890A="</span><span class="sy0">,</span><span class=""></span></li><li class=" even"><span class="">     </span><span class="kw1">"name"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"yarden"</span><span class="sy0">,</span><span class=""></span></li><li class=" odd"><span class="">     </span><span class="st0">"avatar"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"http://avatar_url"</span><span class=""></span></li><li class=" even"><span class="">   </span><span class="br0">}</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">  </span><span class="st0">"message"</span><span class="sy0">:</span><span class=""> </span></li><li class=" even"><span class="">  </span><span class="br0">{</span><span class=""> </span></li><li class=" odd"><span class="">    </span><span class="st0">"type"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"text"</span><span class="sy0">,</span><span class=""></span></li><li class=" even"><span class="">     </span><span class="st0">"text"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"a message to the service"</span><span class="sy0">,</span><span class=""></span></li><li class=" odd"><span class="">     </span><span class="kw1">"media"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"http://download_url"</span><span class="sy0">,</span><span class=""></span></li><li class=" even"><span class="">     </span><span class="st0">"location"</span><span class="sy0">:</span><span class=""></span></li><li class=" odd"><span class="">    </span><span class="br0">{</span><span class=""></span></li><li class=" even"><span class="">      </span><span class="st0">"lat"</span><span class="sy0">:</span><span class=""> </span><span class="nu0">50.76891</span><span class="sy0">,</span><span class=""></span></li><li class=" odd"><span class="">      </span><span class="kw1">"lon"</span><span class="sy0">:</span><span class=""> </span><span class="nu0">6</span><span class="nu0">.11499</span><span class="br0">}</span><span class="sy0">,</span><span class=""></span></li><li class=" even"><span class="">      </span><span class="kw1">"tracking_data"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"tracking data"</span><span class=""></span></li><li class=" odd"><span class="">     </span><span class="br0">}</span><span class=""> </span></li><li class=" even"><span class="">  </span><span class="br0">}</span><span class=""></span></li><li class=" odd"><span class=""></span><span class="br0">}</span></li></ol><pre style="display: none;">{ 
  "event": "message", 
  "timestamp": 1457764197627, 
  "message_token": 4912661846655238145, 
  "sender": 
  { 
    "id": "01234567890A=",
     "name": "yarden",
     "avatar": "http://avatar_url"
   }, 
  "message": 
  { 
    "type": "text",
     "text": "a message to the service",
     "media": "http://download_url",
     "location":
    {
      "lat": 50.76891,
      "lon": 6.11499},
      "tracking_data": "tracking data"
     } 
  }
}</pre><div class="EnlighterJSToolbar"><a class="EnlighterJSInfoButton" title="EnlighterJS Syntax Highlighter"></a><a class="EnlighterJSRawButton" title="Toggle RAW Code"></a><a class="EnlighterJSWindowButton" title="Open Code in new Window"></a><span class="clear"></span></div></div>
<p><em>event</em> = in case of message sent by user event value will be message<br><em>timestamp</em> = time of the event that triggered the callback<br><em>message_token</em> = unique id of message<br><em>sender</em> = sender details (id, name, avatar)<br><em>message</em> = message details like text, media (if any) and so on</p>
<p>In this way we can receive message from user and appropriate message can be sent to user which will be discussed below.</p>
<h3>5. Send message</h3>
<p>In order to send message to user, we need to call a Post request to <em>send_message</em> api as below:</p>
<p><strong>Sending text message:</strong><br>
Url : https://chatapi.viber.com/pa/send_message<br>
Post parameters:</p>
<pre class="EnlighterJSRAW" data-enlighter-language="json" style="display: none;">{
  "auth_token": "455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8", 
  "receiver": "01234567890A=", 
  "type": "text", 
  "text": "a message from pa" 
}</pre><div class="EnlighterJSWrapper enlighterEnlighterJSWrapper"><ol class="hoverEnabled enlighterEnlighterJS EnlighterJS"><li class=" odd"><span class="br0">{</span><span class=""></span></li><li class=" even"><span class="">  </span><span class="kw1">"auth_token"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">  </span><span class="kw1">"receiver"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"01234567890A="</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">  </span><span class="st0">"type"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"text"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">  </span><span class="st0">"text"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"a message from pa"</span><span class=""> </span></li><li class=" even"><span class=""></span><span class="br0">}</span></li></ol><pre style="display: none;">{
  "auth_token": "455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8", 
  "receiver": "01234567890A=", 
  "type": "text", 
  "text": "a message from pa" 
}</pre><div class="EnlighterJSToolbar"><a class="EnlighterJSInfoButton" title="EnlighterJS Syntax Highlighter"></a><a class="EnlighterJSRawButton" title="Toggle RAW Code"></a><a class="EnlighterJSWindowButton" title="Open Code in new Window"></a><span class="clear"></span></div></div>
<p><em>auth_token</em> = The token string provided by Viber on Public Account creation.<br><em>receiver</em> = unique viber user id to whom the message is being sent<br><em>type</em> = Message type (“text” for text messages)<br><em>text</em> = text message to be sent</p>
<p><strong>Sending images:</strong><br>
Url: https://chatapi.viber.com/pa/send_message</p>
<pre class="EnlighterJSRAW" data-enlighter-language="json" style="display: none;">{ 
  "auth_token": "455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8",
  "receiver": "01234567890A=", 
  "type": "picture", 
  "text": "Photo description", 
  "media": "http://www.images.com/img.jpg", 
  "thumbnail": "http://www.images.com/thumb.jpg"
 }</pre><div class="EnlighterJSWrapper enlighterEnlighterJSWrapper"><ol class="hoverEnabled enlighterEnlighterJS EnlighterJS"><li class=" odd"><span class="br0">{</span><span class=""> </span></li><li class=" even"><span class="">  </span><span class="kw1">"auth_token"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8"</span><span class="sy0">,</span><span class=""></span></li><li class=" odd"><span class="">  </span><span class="st0">"receiver"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"01234567890A="</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">  </span><span class="st0">"type"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"picture"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">  </span><span class="st0">"text"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"Photo description"</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">  </span><span class="kw1">"media"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"http://www.images.com/img.jpg"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">  </span><span class="kw1">"thumbnail"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"http://www.images.com/thumb.jpg"</span><span class=""></span></li><li class=" even"><span class=""> </span><span class="br0">}</span></li></ol><pre style="display: none;">{ 
  "auth_token": "455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8",
  "receiver": "01234567890A=", 
  "type": "picture", 
  "text": "Photo description", 
  "media": "http://www.images.com/img.jpg", 
  "thumbnail": "http://www.images.com/thumb.jpg"
 }</pre><div class="EnlighterJSToolbar"><a class="EnlighterJSInfoButton" title="EnlighterJS Syntax Highlighter"></a><a class="EnlighterJSRawButton" title="Toggle RAW Code"></a><a class="EnlighterJSWindowButton" title="Open Code in new Window"></a><span class="clear"></span></div></div>
<p><em>auth_token</em> = The token string provided by Viber on Public Account creation.<br><em>receiver</em> = unique viber user id to whom the message is being sent<br><em>type</em> = Message type (“picture” for image)<br><em>text</em> = photo description (can be null if not required)<br><em>media</em> = URL of image (only JPEG supported)<br><em>thumbnail</em> = reduced image URL (only JPEG supported)</p>
<p>Similarly, we can also send file messages as well.</p>

<center>
<ins class="adsbygoogle" style="display:inline-block;width:336px;height:280px" data-ad-client="ca-pub-2649652639912551" data-ad-slot="3129945437" data-adsbygoogle-status="done"><ins id="aswift_4_expand" style="display:inline-table;border:none;height:280px;margin:0;padding:0;position:relative;visibility:visible;width:336px;background-color:transparent;"><ins id="aswift_4_anchor" style="display:block;border:none;height:280px;margin:0;padding:0;position:relative;visibility:visible;width:336px;background-color:transparent;"><iframe width="336" height="280" frameborder="0" marginwidth="0" marginheight="0" vspace="0" hspace="0" allowtransparency="true" scrolling="no" allowfullscreen="true" onload="var i=this.id,s=window.google_iframe_oncopy,H=s&amp;&amp;s.handlers,h=H&amp;&amp;H[i],w=this.contentWindow,d;try{d=w.document}catch(e){}if(h&amp;&amp;d&amp;&amp;(!d.body||!d.body.firstChild)){if(h.call){setTimeout(h,0)}else if(h.match){try{h=s.upd(h,i)}catch(e){}w.location.replace(h)}}" id="aswift_4" name="aswift_4" style="left:0;position:absolute;top:0;width:336px;height:280px;"></iframe></ins></ins></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script></center>
<h3>6. Send keyboard (Menu)</h3>
<p>The public account API allows sending a custom keyboard using the send_message API, to supply the user with a set of predefined replies or actions. The keyboard can be attached to any message type or sent on it’s on. Once received, the keyboard will appear to the user instead of the device’s native keyboard.</p>
<p>A keyboard can be attached to a message as follows:<br>
Url: https://chatapi.viber.com/pa/send_message<br>
Post parameters:</p>
<pre class="EnlighterJSRAW" data-enlighter-language="json" style="display: none;">{ 
  "auth_token": "455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8", 
  "receiver": "01234567890A=",
  "type":"text",
  "text":"The message",
  "keyboard": { 
    "Type": "keyboard", 
    "BgColor": "#FFFFFF", 
    "Buttons": [ 
    { 
      "Columns": 6, 
      "Rows": 1, 
      "BgColor": "#2db9b9", 
      "BgMediaType": "gif", 
      "BgMedia": "http://www.url.by/test.gif", 
      "BgLoop": true, 
      "ActionType": "open-url", 
      "ActionBody": "www.tut.by", 
      "Image": "www.tut.by/img.jpg", 
      "Text": "Key text", 
      "TextVAlign": "middle", 
      "TextHAlign": "center", 
      "TextOpacity": 60, 
      "TextSize": "regular" 
    },

    { 
      "Columns": 6, 
      "Rows": 1, 
      "BgColor": "#2db9b9", 
      "BgMediaType": "gif", 
      "BgMedia": "http://www.url.by/test.gif", 
      "BgLoop": true, 
      "ActionType": "open-url", 
      "ActionBody": "www.tut.by", 
      "Image": "www.tut.by/img.jpg", 
      "Text": "&lt;b&gt;Key text&lt;/b&gt;", 
      "TextVAlign": "middle", 
      "TextHAlign": "center", 
      "TextOpacity": 60, 
      "TextSize": "regular" 
    } 	
    ] 
  } 
}</pre><div class="EnlighterJSWrapper enlighterEnlighterJSWrapper"><ol class="hoverEnabled enlighterEnlighterJS EnlighterJS" style="display: none;"><li class=" odd"><span class="br0">{</span><span class=""> </span></li><li class=" even"><span class="">  </span><span class="kw1">"auth_token"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">  </span><span class="kw1">"receiver"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"01234567890A="</span><span class="sy0">,</span><span class=""></span></li><li class=" even"><span class="">  </span><span class="st0">"type"</span><span class="sy0">:</span><span class="st0">"text"</span><span class="sy0">,</span><span class=""></span></li><li class=" odd"><span class="">  </span><span class="kw1">"text"</span><span class="sy0">:</span><span class="st0">"The message"</span><span class="sy0">,</span><span class=""></span></li><li class=" even"><span class="">  </span><span class="kw1">"keyboard"</span><span class="sy0">:</span><span class=""> </span><span class="br0">{</span><span class=""> </span></li><li class=" odd"><span class="">    </span><span class="kw1">"Type"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"keyboard"</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">    </span><span class="st0">"BgColor"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"#FFFFFF"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">    </span><span class="kw1">"Buttons"</span><span class="sy0">:</span><span class=""> </span><span class="br0">[</span><span class=""> </span></li><li class=" even"><span class="">    </span><span class="br0">{</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="st0">"Columns"</span><span class="sy0">:</span><span class=""> </span><span class="nu0">6</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="st0">"Rows"</span><span class="sy0">:</span><span class=""> </span><span class="nu0">1</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="kw1">"BgColor"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"#2db9b9"</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="st0">"BgMediaType"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"gif"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="st0">"BgMedia"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"http://www.url.by/test.gif"</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="kw1">"BgLoop"</span><span class="sy0">:</span><span class=""> </span><span class="kw2">true</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="kw1">"ActionType"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"open-url"</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="st0">"ActionBody"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"www.tut.by"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="st0">"Image"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"www.tut.by/img.jpg"</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="kw1">"Text"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"Key text"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="st0">"TextVAlign"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"middle"</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="kw1">"TextHAlign"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"center"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="st0">"TextOpacity"</span><span class="sy0">:</span><span class=""> </span><span class="nu0">60</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="kw1">"TextSize"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"regular"</span><span class=""> </span></li><li class=" odd"><span class="">    </span><span class="br0">}</span><span class="sy0">,</span><span class=""></span></li><li class=" even"><span class=""></span></li><li class=" odd"><span class="">    </span><span class="br0">{</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="kw1">"Columns"</span><span class="sy0">:</span><span class=""> </span><span class="nu0">6</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="st0">"Rows"</span><span class="sy0">:</span><span class=""> </span><span class="nu0">1</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="kw1">"BgColor"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"#2db9b9"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="st0">"BgMediaType"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"gif"</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="kw1">"BgMedia"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"http://www.url.by/test.gif"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="kw1">"BgLoop"</span><span class="sy0">:</span><span class=""> </span><span class="kw2">true</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="st0">"ActionType"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"open-url"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="kw1">"ActionBody"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"www.tut.by"</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="kw1">"Image"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"www.tut.by/img.jpg"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="st0">"Text"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"&lt;b&gt;Key text&lt;/b&gt;"</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="st0">"TextVAlign"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"middle"</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="kw1">"TextHAlign"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"center"</span><span class="sy0">,</span><span class=""> </span></li><li class=" even"><span class="">      </span><span class="kw1">"TextOpacity"</span><span class="sy0">:</span><span class=""> </span><span class="nu0">60</span><span class="sy0">,</span><span class=""> </span></li><li class=" odd"><span class="">      </span><span class="kw1">"TextSize"</span><span class="sy0">:</span><span class=""> </span><span class="st0">"regular"</span><span class=""> </span></li><li class=" even"><span class="">    </span><span class="br0">}</span><span class="">   </span></li><li class=" odd"><span class="">    </span><span class="br0">]</span><span class=""> </span></li><li class=" even"><span class="">  </span><span class="br0">}</span><span class=""> </span></li><li class=" odd"><span class=""></span><span class="br0">}</span></li></ol><pre style="display: block;">{ 
  "auth_token": "455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8", 
  "receiver": "01234567890A=",
  "type":"text",
  "text":"The message",
  "keyboard": { 
    "Type": "keyboard", 
    "BgColor": "#FFFFFF", 
    "Buttons": [ 
    { 
      "Columns": 6, 
      "Rows": 1, 
      "BgColor": "#2db9b9", 
      "BgMediaType": "gif", 
      "BgMedia": "http://www.url.by/test.gif", 
      "BgLoop": true, 
      "ActionType": "open-url", 
      "ActionBody": "www.tut.by", 
      "Image": "www.tut.by/img.jpg", 
      "Text": "Key text", 
      "TextVAlign": "middle", 
      "TextHAlign": "center", 
      "TextOpacity": 60, 
      "TextSize": "regular" 
    },

    { 
      "Columns": 6, 
      "Rows": 1, 
      "BgColor": "#2db9b9", 
      "BgMediaType": "gif", 
      "BgMedia": "http://www.url.by/test.gif", 
      "BgLoop": true, 
      "ActionType": "open-url", 
      "ActionBody": "www.tut.by", 
      "Image": "www.tut.by/img.jpg", 
      "Text": "&lt;b&gt;Key text&lt;/b&gt;", 
      "TextVAlign": "middle", 
      "TextHAlign": "center", 
      "TextOpacity": 60, 
      "TextSize": "regular" 
    } 	
    ] 
  } 
}</pre><div class="EnlighterJSToolbar"><a class="EnlighterJSInfoButton" title="EnlighterJS Syntax Highlighter"></a><a class="EnlighterJSRawButton" title="Toggle RAW Code"></a><a class="EnlighterJSWindowButton" title="Open Code in new Window"></a><span class="clear"></span></div></div>
<p>Image For Keyboard can be:</p>
<figure id="attachment_171" style="max-width: 170px" class="wp-caption aligncenter"><noscript>&lt;IMG class="size-medium wp-image-171 " alt="Image for keyboard(menu)" width="170" height="300" data-sizes="(max-width: 170px) 100vw, 170px" data-srcset="https://i1.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_menu.png?resize=170%2C300 170w, https://i1.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_menu.png?w=301 301w" data-src="https://i1.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_menu.png?resize=170%2C300" src="https://i1.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_menu.png?resize=170%2C300" data-recalc-dims="1"&gt;</noscript><img class="size-medium wp-image-171 lazyloaded" alt="Image for keyboard(menu)" width="170" height="300" data-sizes="(max-width: 170px) 100vw, 170px" data-srcset="https://i1.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_menu.png?resize=170%2C300 170w, https://i1.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_menu.png?w=301 301w" data-src="http://thedebuggers.com/wp-content/uploads/2017/01/viber_menu-170x300.png" sizes="(max-width: 170px) 100vw, 170px" srcset="https://i1.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_menu.png?resize=170%2C300 170w, https://i1.wp.com/thedebuggers.com/wp-content/uploads/2017/01/viber_menu.png?w=301 301w" src="http://thedebuggers.com/wp-content/uploads/2017/01/viber_menu-170x300.png"><figcaption class="wp-caption-text">Viber chat example menu</figcaption></figure><p>All parameters are same as that of sending normal text message except for the <em>param</em> keyboard.<br>
The button array contains array of buttons as per the requirement.</p>
<p><strong>General Keyboard parameters are:</strong><br>
– <em>Type</em>: Required. Type of keyboard display (currently only “keyboard” is available).<br>
– <em>Buttons</em>: Required. It is array containing all keyboard buttons by order.<br>
– <em>BgColor</em>: Optional. Background color of keyboard to be provided HEX value.<br>
– <em>DefaultHeight</em>: Optional. Possible values are true or false.<br><strong> Button Array Parameters</strong><br>
The following parameters can be defined for each button in the “buttons” array separately. Each button must contain at least one of the following optional parameters: text, BgMedia, image, BgColor.<br>
– Columns: button width in columns. possible values 1-6.<br>
– Rows: button height in rows. possible values 1 and 2.<br>
– BgColor: background color to be provided HEX value.<br>
– BgMediaType: type of background media. Possible values: picture or gif.<br>
– BgMedia: url for background media (picture or gif)<br>
– BgLoop: possible values: true or false.<br>
– ActionType: type of action on pressing the button. Possible values: reply or open-url. reply will send reply as normal message and open-url will open a link.<br>
– ActionBody: text to reply if ActionType is reply and link to open if ActionType is open-url.<br>
– Image: url of image to be placed on top of background.<br>
– Text: text to be displayed in button.<br>
– TextVAlign: vertical alignment of text. Possible values: top or middle or buttom.<br>
– TextHAlign: horizontal alignment of text. Possible values: left or center or right.<br>
– TextOpacity: text opacity. Possible values 1-100.<br>
– TextSize: size of text. possible values: small or regular or large.</p>
<p>Button text can support some HTML tags:</p>
<pre class="EnlighterJSRAW" data-enlighter-language="html" style="display: none;">&lt;b&gt;Text Here&lt;/b&gt; Bold
&lt;i&gt;Text Here&lt;/i&gt; Italic
&lt;u&gt; Text Here &lt;/u&gt; Underline
Line Break 
&lt;span style="color: #7f00ff;"&gt;X&lt;/span&gt; Font Color</pre><div class="EnlighterJSWrapper enlighterEnlighterJSWrapper"><ol class="hoverEnabled enlighterEnlighterJS EnlighterJS"><li class=" odd"><span class="kw1">&lt;b</span><span class="kw1">&gt;</span><span class="">Text Here</span><span class="kw1">&lt;/b&gt;</span><span class=""> Bold</span></li><li class=" even"><span class=""></span><span class="kw1">&lt;i</span><span class="kw1">&gt;</span><span class="">Text Here</span><span class="kw1">&lt;/i&gt;</span><span class=""> Italic</span></li><li class=" odd"><span class=""></span><span class="kw1">&lt;u</span><span class="kw1">&gt;</span><span class=""> Text Here </span><span class="kw1">&lt;/u&gt;</span><span class=""> Underline</span></li><li class=" even"><span class="">Line Break </span></li><li class=" odd"><span class=""></span><span class="kw1">&lt;span</span><span class=""> </span><span class="kw2">style</span><span class="kw1">=</span><span class="st0">"color: #7f00ff;"</span><span class="kw1">&gt;</span><span class="">X</span><span class="kw1">&lt;/span&gt;</span><span class=""> Font Color</span></li></ol><pre style="display: none;">&lt;b&gt;Text Here&lt;/b&gt; Bold
&lt;i&gt;Text Here&lt;/i&gt; Italic
&lt;u&gt; Text Here &lt;/u&gt; Underline
Line Break 
&lt;span style="color: #7f00ff;"&gt;X&lt;/span&gt; Font Color</pre><div class="EnlighterJSToolbar"><a class="EnlighterJSInfoButton" title="EnlighterJS Syntax Highlighter"></a><a class="EnlighterJSRawButton" title="Toggle RAW Code"></a><a class="EnlighterJSWindowButton" title="Open Code in new Window"></a><span class="clear"></span></div></div>
<p><strong>Get Public Account Info</strong><br>
In order to get Public account details, you need to call <em>get_account_info</em> api as follows:<br>
url: https://chatapi.viber.com/pa/get_account_info<br>
Post parameters:</p>
<pre class="EnlighterJSRAW" data-enlighter-language="null" style="display: none;">{ 
    "auth_token": "455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8"
}
</pre><div class="EnlighterJSWrapper enlighterEnlighterJSWrapper"><ol class="hoverEnabled enlighterEnlighterJS EnlighterJS"><li class=" odd"><span class="br0">{</span><span class=""> </span></li><li class=" even"><span class="">    </span><span class="st0">"auth_token"</span><span class="">: </span><span class="st0">"455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8"</span><span class=""></span></li><li class=" odd"><span class=""></span><span class="br0">}</span></li></ol><pre style="display: none;">{ 
    "auth_token": "455a0f2c05b4fe54-cb4e33d3200fbbae-95f29ebc06af09a8"
}</pre><div class="EnlighterJSToolbar"><a class="EnlighterJSInfoButton" title="EnlighterJS Syntax Highlighter"></a><a class="EnlighterJSRawButton" title="Toggle RAW Code"></a><a class="EnlighterJSWindowButton" title="Open Code in new Window"></a><span class="clear"></span></div></div>
<p>where auth_token is&nbsp; the token string provided by Viber on Public Account creation.</p>
<p>In this way, you can develop a simple Chat Bot for Viber using PHP. Moreover, it is the starting point to build complex bot. You should try to implement your own to respond to the various messages.</p>
<p><em><strong>Updates</strong>: After having a lot of requests from readers, we have extended the Viber chat bot further with structure messages like keyboard menu, images, links and so on. Please go through the article below to find live example.</em></p>
<p><a href="http://thedebuggers.com/structured-message-keyboard-menu-viber-bot/">Sending structured message and keyboard menu in Viber chat bot</a></p>
<p>&nbsp;</p>

<div class="sharedaddy sd-sharing-enabled"><div class="robots-nocontent sd-block sd-social sd-social-icon-text sd-sharing"><h3 class="sd-title">Share this:</h3><div class="sd-content"><ul><li class="share-twitter"><a rel="nofollow" data-shared="sharing-twitter-162" class="share-twitter sd-button share-icon" href="http://thedebuggers.com/build-viber-chat-bot-6-simple-steps/?share=twitter&amp;nb=1" target="_blank" title="Click to share on Twitter"><span>Twitter</span></a></li><li class="share-facebook"><a rel="nofollow" data-shared="sharing-facebook-162" class="share-facebook sd-button share-icon" href="http://thedebuggers.com/build-viber-chat-bot-6-simple-steps/?share=facebook&amp;nb=1" target="_blank" title="Click to share on Facebook"><span>Facebook<span class="share-count">17</span></span></a></li><li class="share-google-plus-1"><a rel="nofollow" data-shared="sharing-google-162" class="share-google-plus-1 sd-button share-icon" href="http://thedebuggers.com/build-viber-chat-bot-6-simple-steps/?share=google-plus-1&amp;nb=1" target="_blank" title="Click to share on Google+"><span>Google</span></a></li><li class="share-end"></li></ul></div></div></div>
