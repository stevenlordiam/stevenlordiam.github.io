# octopress-weibo
===============

Description
======
It seems like plugin for Octopress. It provides the rake task to post the latest blog to sina weibo automatically. 中文介绍，请访问链接：[Octopress的新浪微博插件](http://agiledon.github.com/blog/2012/12/26/weibo-plugin-for-octopress/)。

Files
======
I create the new folder "_custom" which contains the only one ruby file. You can download it and copy it to the root directory of Octopress. 

To support rake task, I add the customize task into the Rakefile. You can download it and replace the original one directily, or you can open your Rakefile, add the code snippet as below:

    desc "Post the title and url of latest blog to Sina Weibo"
        task :weibo do
        puts "Post the title and url of latest blog to Sina Weibo"
        system "ruby _custom/post_weibo.rb"
    end



Configuration
======
You must add the following configs into the new weibo-config.yml:
    
    access_token: Your access token provided by Sina weibo
    post_template: 我在agiledon.github.com上发表了最新博客《%{blog_title}》，请访问链接：%{blog_url}

What you should do is to customize your post template, but the most important thing is you can't change the variables including %{blog_title} and %{blog_url}.

%{blog_title}: the title of your latest blog. It can support English, Chinese and other languages;
%{blog_url}: the url of your latest blog. 

Don't worry about how to get this information for post_template, this plugin can extract the correct information. 

For example, you create the new post which file name is 2012-12-25-test-demo.markdown, and the title is "测试演示". The content of your weibo post is:

    我在agiledon.github.com上发表了最新博客《测试演示》，请访问链接：http://agiledon.github.com/2012/12/25/test-demo

Notes: You'd better add the file name of weibo-config.yml into your .gitignore file, so that it can let your access-token more safe.

The main url, such as http://agiledon.github.com is come from the value of url in the _config.yml. 

Dependencies
======
My implemention use the "faraday" to send the post request, so you should add the gem dependencies into the Gemfile:

    gem "faraday", "~> 0.8.4"

Then, you might go to the root directory of octopress, run the command to install faraday:

    bundle install

How to use it
=======
If everything is OK, you can run the rake command as below after you finish your new blog:

    rake weibo

It will post the content according to the template in _config.yml to your sina weibo automatically. I strongly suggest you might run it after you make sure you have deployed your new blog successfuly. 

License
======
(The MIT License)

Copyright © 2012 Zhang Yi

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the ‘Software’), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED ‘AS IS’, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


