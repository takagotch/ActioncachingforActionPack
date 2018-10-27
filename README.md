### action-action_caching
ActioncachingforActionPack

---
https://github.com/rails/actionpack-action_caching

```
gem 'actionpack-action_caching'
bundle 
gem install actionpack-action_caching


```


```
class ListsController < ApplicationController
  before_action :authenticate, except: :public
  caches_page :public
  caches_action :index, :show
end

class listsController < ApplicationController
  before_action :authenticate, except: :public
  caches_action :current
  caches_action :archived, expires_in: 1.hour
  caches_action :index, unless: -> { request.format.json? }
  caches_action :show, cache_path: { project: 1 }
  caches_action :histroy, cache_path: -> { request.domain }
  caches_action :feed, cache_path: :user_cache_path
  protected
    def user_cache_path
      if params[:user_id]
        user_list_url(params[:user_id], params[:id])
      else
        list_url(params[:id])
      end
    end
end



```

```
```
