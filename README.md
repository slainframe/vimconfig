# vimconfig

syntax on

colorscheme atom-dark-256

set backspace=2
set laststatus=2
set clipboard=unnamed
set nu

"program execution shortcuts"


noremap <F1> <ESC>:tabprev <CR>
vnoremap <F1> <ESC>:tabprev <CR>
inoremap <F1> <ESC>
 
noremap <F3> <ESC> :w <CR> :make <CR>
inoremap <F3> <ESC> :w <CR> :make <CR>
 
"noremap <F4> <ESC> :w <CR> :!pycodestyle %<.py <CR>
"inoremap <F4> <ESC> :w <CR> :!pycodestyle %<.py <CR>
 
"noremap <F5> <ESC> :w <CR> :!pytest %<.py <CR>
"inoremap <F5> <ESC> :w <CR> :!pytest %<.py <CR>
 
"noremap <F6> <ESC> :!./%< < inp<CR>
"inoremap <F6> <ESC> :!./%< < inp<CR>
 
noremap <F7> <ESC> :w !python3 <CR>
 
"noremap <F7> <ESC> :w <CR> :!avr-gcc -g -std=c99 -O1 -mmcu=atmega328p -o out.elf example.c<CR>
"noremap <F6> <ESC> :w <CR> :!avrdude -v -patmega328p -P /dev/cu.usbmodem14* -c arduino -U flash:w:"out.elf"<CR>
"noremap <F5> <ESC> :w <CR> :!avrdude -v -patmega328p -P /dev/cu.usbmodemHID* -c arduino -U flash:w:"out.elf"<CR>
 
autocmd filetype cpp nnoremap <F9> :w <bar> !g++ -std=c++17 % -o %:r -Wl,--stack,268435456<CR>
autocmd filetype cpp nnoremap <F10> :!%:r<CR>
autocmd filetype cpp nnoremap <C-C> :s/^\(\s*\)/\1\/\/<CR> :s/^\(\s*\)\/\/\/\//\1<CR> $
 
" -pthread
 
"noremap <F9> <ESC> :w <CR> :!g++ -std=c++17 -Wall -Wextra -Wshadow -DONPC -O2 -o %< % && ./%< <CR>
"inoremap <F9> <ESC> :w <CR> :!g++ -std=c++17 -Wall -Wextra -Wshadow -DONPC -O2 -o %< % && ./%< <CR>
 
"noremap <F10> <ESC> :w <CR> :!clang++ -fsanitize=address -std=c++17 -Wall -Wextra -Wshadow -DONPC -O2 -o %< % && ./%< <CR>
"inoremap <F10> <ESC> :w <CR> :!clang++ -fsanitize=address -std=c++17 -Wall -Wextra -Wshadow -DONPC -O2 -o %< % && ./%< <CR>
 
 
"noremap <F10> <ESC> :w <CR> :!g++ -fsanitize=address -std=c++17 -Wall -Wextra -Wshadow -DONPC -O2 -o %< % && ./%< < inp<CR>
"inoremap <F10> <ESC> :w <CR> :!g++ -fsanitize=address -std=c++17 -Wall -Wextra -Wshadow -DONPC -O2 -o "%<" "%" && "./%<" < inp<CR>
 
 
 
"inoremap {<CR> {<CR>}<ESC>k$A<CR>
 
noremap <TAB> %

call plug#begin('~/vimfiles/plugged')
Plug 'scrooloose/nerdtree'
Plug 'itchyny/lightline.vim'
Plug 'tpope/vim-fugitive'
Plug 'vimwiki/vimwiki'
call plug#end()

if has("gui_running")
  if has("gui_gtk2")
    set guifont=Inconsolata\ 12
  elseif has("gui_macvim")
    set guifont=Menlo\ Regular:h14
  elseif has("gui_win32")
    set guifont=Consolas:h11:cANSI
    set guioptions +=m "Hides the menubar
    set guioptions +=T "Hides the toolbar
  endif
endif

" Fugitive vim remaps
nmap <leader>gh :diffget //3<CR>
nmap <leader>gu :diffget //2<CR>
nmap <leader>gs :G<CR>
